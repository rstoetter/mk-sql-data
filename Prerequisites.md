In order to use examples which are connecting to the database you have to create a database / schema and a user, which owns this database or schema. Then you will be able to use the example files

# Using MySQL

Use the program "mysql" in order to execute the SQL commands.

## Create database
```
create database db2phpsite;
use db2phpsite;
```

## Create user
```
CREATE USER 'db2phpsite'@'localhost' IDENTIFIED BY 'db2phpsite'
GRANT ALL ON db2phpsite.* TO 'db2phpsite'@'localhost';
FLUSH PRIVILEGES;
exit
```

## Fill the database
```
mysql -u db2phpsite -pdb2phpsite < examples/mk-sql-data-init-mysql.sql
```

# Using Oracle

The CONNECT-string may vary depending on the Version and the location of the database.

## Install INSTANTCLIENT from ORACLE and sqlplus
[[Install ORACLE INSTANTCLIENT]]

## Install ORACLE oci8 library

[[Install ORACLE oci8]]

## Create a new user ( = schema )

Use the program "sqlplus" in order to execute the SQL commands. sqlplus64 /nolog starts without connecting to a schema.
```
sqlplus64 /nolog

CONNECT system/oracle@192.168.1.65/XE

create user db2phpsite identified by "db2phpsite";

grant dba,resource, connect to db2phpsite;

connect db2phpsite/db2phpsite@192.168.1.65;
```

## Fill the database
```
@ './mk-sql-data-init-oracle.sql';
exit;
```

you can fill the database from the client, too with the command

```
sqlplus64 db2phpsite/db2phpsite@192.168.1.65/XE examples/mk-sql-data-init-oracle.sql
```

