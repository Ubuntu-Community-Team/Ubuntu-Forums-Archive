---
title: "Migration from Oracle 8 (Win) to MySQL (ubuntu)"
date: 2006-10-26
forum: General Help
---

### Post by salvo1 on 2006-10-26
How to run the Migration Toolkit to import a (really big) Oracle database to MySQL???

I tried it with MySQL on Windows but the migration toolkit gives me problems with java...
..in particular i'm looking for a Migration_Toolkit_Easy_To_Install.deb :)

---

### Post by valter on 2006-10-26
By the way MySQL doesn't suport SEQUENCES - I read that there will be problem if you migrate such Oracle database that uses them.

---

### Post by salvo1 on 2006-10-26
I don't think there's SEQUENCES in my Oracle DB (50GB, 164 milions of rows!!).

[This]("http://forums.mysql.com/read.php?104,123082,123082#msg-123082") is the problem:

```

Connecting to source database and retrieve schemata names.
Initializing JDBC driver ...
Driver class Oracle Thin JDBC Driver using SID
Opening connection ...
Connection jdbc:oracle:thin:fidelity/fidelity@192.168.9.143:1521:FID1
Fetching schemata list.
SELECT USERNAME FROM ALL_USERS ORDER BY USERNAME
The list of schema names could not be retrieved (error: 0).
ReverseEngineeringOracle.getSchemata :La lunghezza del tipo è superiore al valore massimo
Details:
oracle.jdbc.driver.DatabaseError.throwSqlException(DatabaseError.java:125)
oracle.jdbc.driver.DatabaseError.throwSqlException(DatabaseError.java:162)
oracle.jdbc.driver.DatabaseError.check_error(DatabaseError.java:885)
oracle.jdbc.driver.T4CMAREngine.buffer2Value(T4CMAREngine.java:2231)
oracle.jdbc.driver.T4CMAREngine.unmarshalUB2(T4CMAREngine.java:1048)
oracle.jdbc.driver.T4CTTIdcb.receiveCommon(T4CTTIdcb.java:112)
oracle.jdbc.driver.T4CTTIdcb.receive(T4CTTIdcb.java:95)
oracle.jdbc.driver.T4C8Oall.receive(T4C8Oall.java:591)
oracle.jdbc.driver.T4CStatement.doOall8(T4CStatement.java:112)
oracle.jdbc.driver.T4CStatement.execute_for_describe(T4CStatement.java:351)
oracle.jdbc.driver.OracleStatement.execute_maybe_describe(OracleStatement.java:896)
oracle.jdbc.driver.T4CStatement.execute_maybe_describe(T4CStatement.java:383)
oracle.jdbc.driver.OracleStatement.doExecuteWithTimeout(OracleStatement.java:986)
oracle.jdbc.driver.OracleStatement.executeQuery(OracleStatement.java:1125)
com.mysql.grt.modules.ReverseEngineeringOracle.getSchemata(ReverseEngineeringOracle.java:52)
sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
java.lang.reflect.Method.invoke(Unknown Source)
com.mysql.grt.Grt.callModuleFunction(Unknown Source)

```

---

### Post by marianom on 2006-10-26
Well, I'm not very good with italian but it seems that some datatype column was expected with a certain precision and you get a bigger one.
Since this happens when you're retrieving data from an oracle's data dictionary table it really really looks bad. 

You should be checking this problem in the appropiate mysql forum. Sure there are gurus there that can help you out.

---

### Post by marianom on 2006-10-26
Upps sorry for that. Now I see you already posted in a mysql forum.

Anyway look that the instruction that raises the error is this one:
SELECT USERNAME FROM ALL_USERS ORDER BY USERNAME

In my Oracle 10g that column is defined as varchar2(30). 
I cannot recall how long was in 8i but maybe the java class is expecting a lower value.
Which is the longest username you have in that table?

---

