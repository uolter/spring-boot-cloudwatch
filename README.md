# spring-boot-cloudwatch
Simple Spring boot application configured to send metrics to AWS Cloudwatch


## Build the application with docket

```bash
docker build -t springboot-cloudwatch .
```

## Run the application locally 

To run the application locally you have to pass to the docker run command the AWS keys.
It is also recommented to assume a role which has attached polices to Put Metrics in CloudWatch

Someting like:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "Stmt1660902398464",
      "Action": [
        "cloudwatch:PutMetricData"
      ],
      "Effect": "Allow",
      "Resource": "*"
    }
  ]
}
```


```bash
docker run -it -p 8080:8080 -p 8081:8081 --rm \
-e AWS_REGION=eu-central-1 \
-e AWS_ACCESS_KEY_ID="<your access key>" \
-e AWS_SECRET_ACCESS_KEY="<your secret key>" \
-e AWS_SESSION_TOKEN="<your session token>" springboot-cloudwatch 
```


## TODO publish and run the image in ECS 
