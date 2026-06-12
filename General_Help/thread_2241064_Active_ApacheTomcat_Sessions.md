---
title: "Active Apache/Tomcat Sessions"
date: 2014-08-23
forum: General Help
---

### Post by airforceboricua33 on 2014-08-23
Hello All,

I am trying to figure out how I can see if anyone is currently connected to my webserver.  Is there an apache log and/or a tomcat log where I can see the active sessions?

Thank you for your help.

---

### Post by Habitual on 2014-08-24
Unless defaults have been altered, both should be under /var/log/
/var/log/httd/
and tomcat may be /var/log/tomcat6 or just /var/log/tomcat

```
netstat -pluant | grep LISTEN | grep -e httpd -e java
```
to show daemons that are listening.

---

