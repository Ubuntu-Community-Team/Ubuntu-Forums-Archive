---
title: "Setting up mysql-server-5.7 whenever I try to install something"
date: 2017-10-20
forum: General Help
---

### Post by porjazovskideni on 2017-10-20
Hello everyone,

I have a weird problem. Whenever I try to install something I get this:
 ```
Setting up mysql-server-5.7 (5.7.18-0ubuntu0.16.10.1) ...update-alternatives: error: alternative path /etc/mysql/mysql.cnf doesn't exist
dpkg: error processing package mysql-server-5.7 (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 mysql-server-5.7
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
and I am not sure why it's trying to set up the mysql server when the things that I try to install have nothing to do with mysql. This started happening when I tried to remove mysql server I had previously installed.
Does anyone know how to resolve this?

**EDIT**

I was able to completely remove the mysql server and after that the problem is gone

---

