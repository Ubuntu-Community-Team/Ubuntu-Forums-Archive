---
title: "Connecting to MySql using ODBC"
date: 2008-01-22
forum: General Help
---

### Post by ThommasO on 2008-01-22
I am new to Linux and have just installed Ubuntu 7.10. The web-server and the database works OK, I can use phpMyAdmin over the LAN, but when I try to set up an ODBC connection(driver version 3.51 under Windows) I get Error:
Request returned an SQL error(10061).
Would appreciate some help.

ThommasO.

---

### Post by gvartser on 2008-01-22
Is the user your trying to connect as granted to logon using password and from other sources then 127.0.0.1.

/g

---

### Post by ThommasO on 2008-01-23
The user is root, which I can use to log on to the DB locally, and I'm connecting from another PC on the LAN(i.e. 192.168.1.x)
I use the ip-address of the server when trying to connect. Have tried the name as well. No luck

---

