# Empty a versioned S3 Bucket
- Source: https://towardsthecloud.com/aws-cli-empty-s3-bucket#:~:text=If%20the%20versioning%20is%20disabled,then%20proceed%20to%20delete%20it.

aws s3api delete-objects --bucket my-bucket \ 
  --delete "$(aws s3api list-object-versions \
  --bucket "my-bucket" \
  --output=json \
  --query='{Objects: Versions[].{Key:Key,VersionId:VersionId}}')"

- notes: replace my-bucket with the name of the S3 bucket