---
title: "Unable to access HTML management interface in Apache Tomcat 9"
date: 2018-06-07
forum: General Help
---

### Post by tuddungoggo on 2018-06-07
Hello everyone,

Unfortunately, I am unable to access the HTML Management interface of Apache Tomcat. I did add the user name and role to the users.xml file as follows:

```

<tomcat-users xmlns="http://tomcat.apache.org/xml"
              xmlns: xsi="http://www.w3.org/2001/XMLSchema-instance"
              xsi:schemaLocation="http://tomcat.apache.org/xml tomcat-users.xsd"
              version="1.0">
<!--
  NOTE:  By default, no user is included in the "manager-gui" role required
  to operate the "/manager/html" web application.  If you wish to use this app,
  you must define such a user - the username and password are arbitrary. It is
  strongly recommended that you do NOT use one of the users in the commented out
  section below since they are intended for use with the examples web
  application.
-->
  <role rolename="tomcat"/>
  <role rolename="role1"/>
  <role rolename="manager-gui"/>
  <role rolename="manager-script"/>
  <user username="lamidotijjo" password="s3cret" roles="manager-gui,manager-script,admin-gui"/>
```

What exactly is going on that is preventing from being able to log into the manager HTML GUI?

---

### Post by QIII on 2018-06-07
Hello!

Please enclose code, terminal commands and terminal output in code tags.  This preserves formatting and makes your posts easier to read.

To use code tags:

1.  Either click the # button in the toolbar, position your cursor between the code tags that appear and type or past your text; or type or paste your text, highlight it and then click the # button.

2.  Type [noparse]```
[/noparse] before your text and [noparse]
```[/noparse] after your text.  The square brackets are required.

Thanks.

---

### Post by tuddungoggo on 2018-06-07
Thank you, I will most definitely do that next time.

---

### Post by tuddungoggo on 2018-06-08
No one yet? I truly am stuck. If it helps at all, this is for Tomcat 9. I followed the instructions here: [https://www.digitalocean.com/community/tutorials/how-to-install-apache-tomcat-8-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-apache-tomcat-8-on-ubuntu-16-04)

---

