---
title: "Jdbc"
date: 2005-10-16
forum: General Help
---

### Post by comradevik on 2005-10-16
hi 
 I have 
```
java -version
java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)

```
i'm trying to connect to MySQL but i get the following error 

```
 No suitable driver
        at java.sql.DriverManager.getConnection(DriverManager.java:545)
        at java.sql.DriverManager.getConnection(DriverManager.java:171)
        at Connect.main(Connect.java:10)
```

how do I install the driver.. i installed libmysql-java from apt-get and restarted mysql but it didnt help

---

### Post by comradevik on 2005-10-16
here is my classpath to the mysql-conector

```
root@ubuntu:/home/victor/Desktop/java# export
declare -x CLASSPATH="/var/www/mysqlcon/mysql-connector-java-3.1.11-bin.jar:"
```

---

### Post by comradevik on 2005-10-16
is there anything i can do ?

---

### Post by matthurne on 2005-11-03
The libmysql-java package installs the jar to

```

/usr/share/java/mysql-3.1.7.jar

```

with a symlink:

```

/usr/share/java/mysql.jar

```

So add the symlink (the latter path) to your classpath - you'd probably want to do it via your /etc/profile - add:

```

CLASSPATH=$CLASSPATH:/usr/share/java/mysql.jar
export CLASSPATH

```

and then to put it into effect immediately:

```

username@host:~$  source /etc/profile

```

---

### Post by jvictor on 2005-11-04
I'd say u must add the CLASSPATH entry and export it into ur .bashrc file ..

---

