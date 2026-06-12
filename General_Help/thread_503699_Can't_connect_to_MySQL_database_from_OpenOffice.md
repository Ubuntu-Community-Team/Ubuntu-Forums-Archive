---
title: "Can't connect to MySQL database from OpenOffice"
date: 2007-07-18
forum: General Help
---

### Post by Zhanna on 2007-07-18
(I posted this earlier in the wrong forum but don't see a way to move it, sorry.)

I'm using Ubuntu 7.04.  Trying to connect to an existing remote MySQL database through OpenOffice's database application.  My datasource URL and authentication information are correct (I have a WinXP machine that connects just fine), but I'm unable to connect from Ubuntu.  I get the following error:

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
   at com.mysql.jdbc.SingleByteCharsetConverter.initCharset(SingleByteCharsetConverter.java:108 )
   at com.mysql.jdbc.SingleByteCharsetConverter.getInstance(SingleByteCharsetConverter.java:86)
   at com.mysql.jdbc.StringUtils.getBytes(StringUtils.java:600)
   at com.mysql.jdbc.ByteArrayBuffer.writeStringNoNull(ByteArrayBuffer.java:544)
   at com.mysql.jdbc.MysqlIO.sqlQueryDirect(MysqlIO.java:1660)
   at com.mysql.jdbc.Connection.execSQL(Connection.java:3020)
   at com.mysql.jdbc.Connection.configureClientCharacterSet(Connection.java:2343)
   at com.mysql.jdbc.Connection.initializePropsFromServer(Connection.java:3748 )
   at com.mysql.jdbc.Connection.createNewIO(Connection.java:2585)
   at com.mysql.jdbc.Connection.<init>(Connection.java:1485)
   at com.mysql.jdbc.NonRegisteringDriver.connect(NonRegisteringDriver.java:266)


** END NESTED EXCEPTION **

:confused:  I can't find anything helpful online.  Does anyone have any ideas? 

Thanks!

Zhanna

---

### Post by SDDrew on 2007-07-24
Hi Zhanna,

We have identical problems, apparently!  Have you found a solution yet?

As I wrote in my problem description, other connections to the database (via MySQLdb in Python, for instance) work fine for me, so I'm wondering if OpenOffice has some default encoding (double-byte/UTF8?) which has difficulties digesting data for the purposes of connecting to an external data source...

I'd be interested in hearing from you if you solve this.

Simon

---

### Post by Milflyboy on 2007-09-17
I'm having the exact same problem, only running Fedora 6. (I am a kubuntu user at home, though :-p)

I'm using the MySQL JDBC connector (version 5.0.7), OpenOffice 2.02 (I don't have permissions to upgrade it-- work machine), and MySQL community server version 5.0.45.

The database uses latin1 (ISO-8859-1) for everything. Specifying that character set in the connection settings in Base doesn't help. I've played around with it and only get this error when the password entered is correct. If I change any part of it, I get the expected error 1045 (access denied).

From this, I take away that its not the encoding of the password that's the problem, it's in the JDBC connector (or OOo-- I don't know where one stops and the other starts) not recognizing the encoding of whatever the server's response is to a *successful* login.

Searching on OpenOffice.org hasn't gotten me anywhere. The detail message in the error message is "null".

Aware that this is an ubuntu forum, anyone have any ideas?

---

### Post by YetiCGN on 2007-10-26
I had the same problem after updating from Feisty to Gutsy. After 2 hours of googling today I finally found the solution here: [http://bugs.mysql.com/bug.php?id=29636](http://bugs.mysql.com/bug.php?id=29636)

The update overwrote /etc/mysql/my.cnf, which needs the default-character-set entry so that this exception is not thrown. Add "default-character-set=utf8" to both the client and [mysqld] section and it should work (does for me).

Kind regards,
Yeti

---

