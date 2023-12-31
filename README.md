# PostgreSQL to SQL Server Data Migration Lambda Function (Python 3.7)

This Python script is designed to perform data migration from a PostgreSQL database to a SQL Server database, with the ability to batch copy data to improve performance. The script includes functions to connect to both databases, create tables, and copy data from PostgreSQL to SQL Server. It's intended to be used as an AWS Lambda function for serverless data migration.

## Prerequisites

Before using this script, ensure that you have:

- Python environment with the necessary libraries (`pyodbc` and `psycopg2`) installed.
- Access to the source PostgreSQL database and target SQL Server database.
- AWS Lambda set up with appropriate permissions to access both databases.

## Configuration

Make sure to set up the necessary environment variables for your Lambda function. The following environment variables are required:

### PostgreSQL Configuration:
- `POSTGRES_HOST`: Hostname or IP address of the PostgreSQL database.
- `POSTGRES_PORT`: Port number for the PostgreSQL database.
- `POSTGRES_DBNAME`: Name of the PostgreSQL database.
- `POSTGRES_USER`: Username to access the PostgreSQL database.
- `POSTGRES_PASSWORD`: Password for the PostgreSQL database.

### SQL Server Configuration:
- `SQL_SERVER_HOST`: Hostname or IP address of the SQL Server database.
- `SQL_SERVER_DBNAME`: Name of the SQL Server database.
- `SQL_SERVER_USER`: Username to access the SQL Server database.
- `SQL_SERVER_PASSWORD`: Password for the SQL Server database.

## Usage

This script provides several functions for copying data. You can customize which tables to copy and the batch size for copying data. Ensure that the script is triggered appropriately, either through an event or manually.

## Important Notes

- Be cautious when handling sensitive data and environment variables in AWS Lambda.
- Adjust batch sizes and WHERE clauses as needed to optimize data migration for your specific use case.

## Example Usage

Here's an example of how you can use this script in your Lambda function handler:

```python
def lambda_handler(event, context):
   # AWS RDS PostgreSQL Database Configuration
    postgres_host = os.environ.get('POSTGRES_HOST')
    postgres_port = os.environ.get('POSTGRES_PORT')
    postgres_dbname = os.environ.get('POSTGRES_DBNAME')
    postgres_user = os.environ.get('POSTGRES_USER')
    postgres_password = os.environ.get('POSTGRES_PASSWORD')

    # SQL Server Database Configuration
    sql_server_host = os.environ.get('SQL_SERVER_HOST')
    sql_server_dbname = os.environ.get('SQL_SERVER_DBNAME')
    sql_server_user = os.environ.get('SQL_SERVER_USER')
    sql_server_password = os.environ.get('SQL_SERVER_PASSWORD')

    # ... (rest of the code)

    return {
        'statusCode': 200,
        'body': 'Data copied successfully!'
    }
```
