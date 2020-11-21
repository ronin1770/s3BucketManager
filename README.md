# s3BucketManager
This is a simple project that allows users to create a bucket on AWS S3, upload local files to s3 bucket (filterable by extension type), get the list of files in the bucket.

# Prerequisites
  
Python 3.6+
pip 9.0.1 (atleast)
Boto3 Python package 
AWS Credentials (APP KEY and APP KEY SECRET) stored in credentials file

# Operations allowed

This library allows you to:
  1. Create Bucket
  2. Upload files from local directory to your bucket (filterable by file extension)
  3. Get the list of files in your bucket
  
# Sample initialization script:

    if __name__ == "__main__":
      sbm = s3BucketManager()
      
      # Add the extension you want to be uploaded to the bucket
      filter = [".mpg", ".avi", ".mp3"]
      bucket_name = "<BUCKET_NAME>"

      sbm.set_input_dir("<SET INPUT DIRECTORY WHERE FILES TO BE UPLOADED ARE KEPT>")
      bucket = sbm.create_s3_bucket(bucket_name)

      if bucket != None:
        returnval = sbm.upload_files_to_bucket(bucket_name, filter)
        print(returnval)


      print( sbm.get_files_in_bucket(bucket_name))
