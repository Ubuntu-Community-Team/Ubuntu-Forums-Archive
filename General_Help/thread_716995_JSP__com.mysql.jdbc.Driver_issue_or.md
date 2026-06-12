---
title: "JSP  com.mysql.jdbc.Driver issue?? or ??"
date: 2008-03-06
forum: General Help
---

### Post by Cnk on 2008-03-06
I've been using Ubuntu for a while, anyway, I'm working on a JSP project for now.
I'm using Apache Tomcat, no problem with that, I'm also able to create JSP files as well. 
My problem is that, I'm not able to make a connection between my JSP files and the database I use( MySQL).
I've set my classpath as: 

```
export CLASSPATH=$CLASSPATH:/usr/share/java/mysql-connector-java-5.0.4.jar
```

I ve written a regular java code which make me reach my datas on myDB. But I couldn't make it with JSP.
I'm having: 

```
org.apache.jasper.JasperException: An exception occurred processing JSP page /project/register.jsp at line 15
```

which points this line :     Class.forName("com.mysql.jdbc.Driver");
Could you please help to fix it ?

Thnx...

---

