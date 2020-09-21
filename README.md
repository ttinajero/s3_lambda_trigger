# s3_lambda_trigger

import json
import boto3

#os.environ['AWS_DEFAULT_REGION'] = 'us-west-2'

s3 = boto3.resource('s3')

def lambda_handler(event, context):

	#Trae datos del objeto o archivo puesto en S3
    for record in event['Records']:
		bucket = record['s3']['bucket']['name']
		archivo = record['s3']['object']['key']

        print("BUCKET: "+str(bucket))
        print("ARCHIVO: "+str(archivo))

    #Acceder al archivo como objeto
    obj = s3.get_object(Bucket = bucket, Key = archivo)


	return {
		'statusCode': 200
	}
