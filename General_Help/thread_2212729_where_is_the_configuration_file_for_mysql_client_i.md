---
title: "where is the configuration file for mysql client in ubuntu 12.04.4?"
date: 2014-03-22
forum: General Help
---

### Post by Hodor on 2014-03-22
Hi
I'm trying to set up a lampp on a new machine (ubuntu 12.04.4 32 bit).  Lampp seems to be working ok (installed XAMPP package) but I can't connect to mysql server (it is running) using the mysql client.

When I try to start the client (installed separately, obviously) I get an error:
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock'

Looking at MySQL server configuration file: it expects the socket at /opt/lampp/var/mysql/myql.sock

Am I correct in thinking that I need to change the MySQL client configuration to align with the MySQL server configuration?
What is the easiest way to do this (or otherwise solve the problem if I'm on the wrong track).
Thanks

---

### Post by Dave_L on 2014-03-22
Instead of using XAMPP, it's better to use this method:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by Hodor on 2014-03-23
> **Dave_L said:**
> Instead of using XAMPP, it's better to use this method:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Thanks.  I'll try this - I hope you are correct since removing my XAMPP installation is not going to be fun.

---

### Post by Dave_L on 2014-03-23
I haven't used XAMPP for a long time, but if I recall correctly, it keeps all its files in its own directory. If that's still the case, it should be easy to remove. Or instead of removing it immediately, you could simply ensure that its services (mysql and apache) are stopped. Then XAMPP shouldn't conflict with lamp-server.

---

### Post by meems on 2014-03-23
mysql -u (user) -p -S /path/to/MySQL.sock

---

### Post by Hodor on 2014-03-24
> **meems said:**
> mysql -u (user) -p -S /path/to/MySQL.sock

Thanks very much meems.

---

