---
title: "exception in jdbc with mysql"
date: 2005-05-12
forum: General Help
---

### Post by cristianommxp on 2005-05-12
I'm trying to acess a mysql database with JDBC, but Java is generating an exception:

-----------------------------------------------------------------------------------------------------------------------------
java.sql.SQLException: null,  message from server: "Host 'localhost.localdomain' is not allowed to connect to this MySQL server"
	at com.mysql.jdbc.MysqlIO.doHandshake(MysqlIO.java:1023)
	at com.mysql.jdbc.Connection.createNewIO(Connection.java:1699)
	at com.mysql.jdbc.Connection.<init>(Connection.java:408)
	at com.mysql.jdbc.NonRegisteringDriver.connect(NonRegisteringDriver.java:270)
	at java.sql.DriverManager.getConnection(DriverManager.java:525)
	at java.sql.DriverManager.getConnection(DriverManager.java:171)
	at XTeste.main(XTeste.java:31)
-----------------------------------------------------------------------------------------------------------------------------

So, What do I have to do? What's the solution?

10ks for any help.

Cristiano

---

