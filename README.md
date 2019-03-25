# Informix CDC Java client
This is an Informix CDC client that allows you to capture and unserialize changes on one or multiple tables of the database

It implements methods described by IBM in this sections: https://www.ibm.com/support/knowledgecenter/en/SSGU8G_12.1.0/com.ibm.cdc.doc/ids_cdc_057.htm

# Features - Work in progress
This project is still a work in progress, some data types are not correctly unserialized. Feel free to fork this project.

| Data type | Status | Comment |
|-----------|--------|---------|
| CHAR | Supported ||
| SMALLINT | Supported ||
| INTEGER | Supported ||
| FLOAT | Supported ||
| SMALLFLOAT | Supported ||
| DECIMAL | Supported ||
| SERIAL | Not supported | Unit test fails and needs to be adapted |
| DATE | Not supported ||
| MONEY | Supported ||
| DATETIME | Not supported | Supported up to "YEAR TO SECONDS" precision |
| VARCHAR | Supported ||
| NCHAR | Supported ||
| NVARCHAR | Supported ||
| INT8 | Not supported ||
| SERIAL8 | Supported | Unit test fails and needs to be adapted |
| LVARCHAR | Supported ||
| BOOLEAN | Supported ||
| BIGINT | Not supported ||

A unit test is provided to test the various data types.

Use the provided docker-compose file to launch an Informix database instance, and use this command to create the CDC schema before running the test.
```bash
dbaccess -e informix < $INFORMIXDIR/etc/syscdcv1.sql
```

# Implementation details

Implementation for the CDC client is loosely based on sources published by pushtechnology: https://www.programcreek.com/java-api-examples/index.php?source_dir=adapters-master/cdc/src/com/pushtechnology/diffusion/api/adapters/cdc/CDCConnection.java#

Implementation for the data unserializing is adapted from IBM's C sample: https://www.ibm.com/support/knowledgecenter/fr/SSGU8G_11.50.0/com.ibm.cdc.doc/ids_cdc_060.htm
