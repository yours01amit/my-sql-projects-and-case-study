# !pip install kaggle
# import kaggle 

# !kaggle datasets download ankitbansal06/retail-orders -f orders.csv

download the dataset in zip file
now we have to unzip file


import zipfile
zip_ref = zipfile.ZipFile('orders.csv.zip')
zip_ref.extractall() # extract file to dir
zip_ref.close()

import pandas as pd
df = pd.read_csv('orders.csv',na_values=['Not Available', 'unknown'])

# clean the dataset 


# Load the dataset into mysql database
import pymysql
from sqlalchemy import create_engine
import cryptography


# create engine

engine = create_engine('mysql+pymysql://root:amitkumar@localhost:3306/myretailorderdata')


df.to_sql(name='retail_orders', con=engine, index=False, if_exists='append')


import pandas as pd
import mysql.connector

conn = mysql.connector.connect(
        host='localhost',
        user='root',  # Change this to your MySQL username
        password='password',  # Change this to your MySQL password
        database='myretailorderdata'  # Change this to your database name
    )

query = "SELECT * FROM retail_orders"  # Replace with your SQL query
df = pd.read_sql_query(query, conn)
