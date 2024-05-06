# pycodes
Realtime use cases of s3 bucket copy to dynamo_db tabe using lamda
import json
import urllib.parse
import boto3

dynamodb = boto3.resource('dynamodb')
table = dynamodb.Table('sample_table')


def lambda_handler(event, context):
    s3 = boto3.client('s3')
    copy_source = {
        'Bucket': 'hanu234',
        'Key': 'newfile1.txt'
    }
#s3.meta.client.copy(newfile1.txt, 're6969', 'newtxt.txt')
    a = s3.list_objects(Bucket='re6969')
    b = (a['Contents'][0]['Key'])
    dynamodb_item = {'H': b}
    table.put_item(Item=dynamodb_item)
