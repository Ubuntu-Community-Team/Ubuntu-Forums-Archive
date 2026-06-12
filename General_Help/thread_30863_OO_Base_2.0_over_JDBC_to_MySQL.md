---
title: "OO Base 2.0 over JDBC to MySQL"
date: 2005-04-30
forum: General Help
---

### Post by aburda on 2005-04-30
Hello,

        I'm trying to get JDBC up and running but not having too much luck.  I already have Java installed and can run Eclipse.  From what I understand to get the JDBC driver installed all I have to do is setup the CLASSPATH variable and have it point to the JDBC driver.

I added the following to my bash.bashrc in /etc

CLASSPATH=$JAVA_HOME:$JAVA_HOME/mysql-connector-java-3.1.8-bin.jar
export CLASSPATH

I copied the jar file to that location but still either in MyEclipse or in OO Base 2.0 when I test the driver (com.mysql.jdbc.Driver) it says the driver couldn't be loaded.  Am I missing something?

I can see the CLASSPATH is set when I type 'env' in a shell.  I have given 777 permissions on the file so that can't be the problem.  Any advice much appreciated.


    Thanks


    Aaron

---

### Post by petertc on 2005-05-01
this is just a quick thought, when i was trying to install OO2 beta i had to install the latest java environment for it to work , the olde version with linux wont work, even thoughthey do with Windows.

---

