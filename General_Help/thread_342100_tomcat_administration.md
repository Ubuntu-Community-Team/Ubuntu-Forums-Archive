---
title: "tomcat administration"
date: 2007-01-19
forum: General Help
---

### Post by mitjab on 2007-01-19
what is username and password for tomcat administration by default?

thx

---

### Post by mitjab on 2007-01-22
anyone?

---

### Post by HappyClam on 2007-01-22
$CATALINA_HOME/conf/tomcat-users.xml:

<user username="tomcat" password="tomcat" roles="admin,manager"/> 

You should change it ASAP.

---

