# NodeJS Serverless Framework Template

## Local development

To start offline development

`sls offline start`

Components that will start:

- ### Serverless offline
  - Handles HTTP requests to localhost like the API gateway
- ### DynamoDB 
  - Creates an empty DynamoDB table running locally. Can be viewed and manipulated by the code or the [NoSQL Workbench](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/workbench.settingup.html)
- ### Offline S3
  - Makes a local directory act like an S3 bucket
  - Can be used to
    - Create and work with an ingestion/input bucket
    - Create and work with an output bucket
  - **Usage**
    - aws configure --profile s3local
      - AWS Access Key ID: S3RVER
      - AWS Secret Access Key: S3RVER
    - To copy a local file to the offline bucket
      - `aws --endpoint http://localhost:4569 s3 cp ~/data.csv s3://test-bucket/userdata.csv --profile s3local`

## Invoke functions locally

*The funtion does NOT have to be deployed to run it locally*

`sls invoke local --function hello --path test-events/sqs/fifo-event.json`

This invokes the function named `hello` with the JSON at `test-events/sqs/fifo-event.json` as the invocation event.