---
title: "Does not work ODBC to DB2"
date: 2006-11-14
forum: General Help
---

### Post by rsz on 2006-11-14
Hi All!

I would like to connect to DB2 database(AS400) from my ubuntu box with ODBC.
First of all, i've installed some packages (iodbc, unixodbc, php5odbc).
After that i've installed "DB2 run time Client" fom IBM, 
and edit odbc.ini and odbcinst.ini.
--------------------------------------------------------------
My **odbcinst.ini**:
[DB2]
Description = DB2 driver for Linux
Driver      = /opt/IBM/db2/V8.1/lib/libdb2.so
Fileusage   = 3
[ODBC]
Trace =yes
Tracefile = /opt/IBM/odbctrace.log
--------------------------------------------------------------
My **odbc.ini**:
[ODBC Data Sources]
TEST = IBM DB2 ODBC DRIVER
[TEST]
Driver = /opt/IBM/db2/V8.1/lib/libdb2.so
--------------------------------------------------------------

I've tried to use ODBC from a very simple PHP script, but the odbc coudn't open the libdb2.so.
Here is the error message:

Warning: odbc_connect() [function.odbc-connect]: SQL error: [unixODBC][Driver Manager]Can't open lib '/opt/IBM/db2/V8.1/lib/libdb2.so' : /opt/IBM/db2/V8.1/lib/libdb2.so: cannot open shared object file: No such file or directory, SQL state 01000 in SQLConnect in /var/www/szabi/odbc.php on line 3

Thanks in advance!

---

