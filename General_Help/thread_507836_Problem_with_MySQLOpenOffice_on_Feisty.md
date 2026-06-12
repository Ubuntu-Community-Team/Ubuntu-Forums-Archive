---
title: "Problem with MySQL/OpenOffice on Feisty"
date: 2007-07-23
forum: General Help
---

### Post by SDDrew on 2007-07-23
Hi,

I'm trying to get OpenOffice to access a database, using the JDBC database driver. The connection fails...

> 
The connection to the data source "einvoice" could not be established.

SQL Status: S1000

Error during query: Unexpected Exception: java.io.CharConversionException message given: null

Nested Stack Trace:


** BEGIN NESTED EXCEPTION ** 

java.io.CharConversionException

STACKTRACE:

java.io.CharConversionException
   at gnu.gcj.convert.Input_iconv.read(libgcj.so.70)
   at java.lang.String.init(libgcj.so.70)
   at java.lang.String.<init>(libgcj.so.70)
   at com.mysql.jdbc.SingleByteCharsetConverter.<init>(SingleByteCharsetConverter.java:153)
   at com.mysql.jdbc.SingleByteCharsetConverter.initCharset(SingleByteCharsetConverter.java:108)
   at com.mysql.jdbc.SingleByteCharsetConverter.getInstance(SingleByteCharsetConverter.java:86)
   at com.mysql.jdbc.Connection.getCharsetConverter(Connection.java:3478)
   at com.mysql.jdbc.StringUtils.getBytes(StringUtils.java:615)
   at com.mysql.jdbc.Buffer.writeStringNoNull(Buffer.java:655)
   at com.mysql.jdbc.MysqlIO.sqlQueryDirect(MysqlIO.java:1686)
   at com.mysql.jdbc.Connection.execSQL(Connection.java:3250)
   at com.mysql.jdbc.Connection.configureClientCharacterSet(Connection.java:2514)
   at com.mysql.jdbc.Connection.initializePropsFromServer(Connection.java:4112)
   at com.mysql.jdbc.Connection.createNewIO(Connection.java:2762)
   at com.mysql.jdbc.Connection.<init>(Connection.java:1553)
   at com.mysql.jdbc.NonRegisteringDriver.connect(NonRegisteringDriver.java:285)


** END NESTED EXCEPTION **

The driver is correctly registered, according to the wizard, and the database is accessible through both MySQL and Python using the MySQLdb module.  What am I doing wrong?

---

