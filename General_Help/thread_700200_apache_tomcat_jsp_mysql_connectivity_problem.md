---
title: "apache tomcat jsp mysql connectivity problem"
date: 2008-02-18
forum: General Help
---

### Post by md_imranullah on 2008-02-18
Apache tomcat error on fedora 8. ClassNotFoundException sql exception:No suitable driver found for jdbc:mysql:
hi people,
i have installed apache tomcat on fedora 8. Using javac if i execute a program iam able to establish the connection with the mysql database. but when the same code is run in the jsp with modifications it doesnt run throws out an error like this

"ClassNotFoundException sql exception:No suitable driver found for jdbc:mysql://localhost/test"

I have placed the driver in the lib folder of the jdk installation.

---

### Post by kpkeerthi on 2008-02-18
> 
"ClassNotFoundException sql exception:No suitable driver found for jdbc:mysql://localhost/test"

I have placed the driver in the lib folder of the jdk installation.


The best place to keep the JARs a web-application is dependent on is WEB-INF/lib folder.
Try copying mysql jdbc JAR file to <YOUR-WEB-APP>/WEB-INF/lib folder.

---

