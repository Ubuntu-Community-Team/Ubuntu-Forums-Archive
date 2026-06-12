---
title: "Myth 0.20 upgrade issue with Mysql"
date: 2006-09-13
forum: General Help
---

### Post by Twiggy794 on 2006-09-13
I've had this problem before with Myth 0.19, but I can't seem to figure out what's up here.  Basically I had a machine as a backend, now this new machine is my backend and I'm trying to upgrade mythtv-database but I get this error when it tries to configure:

```
Setting up mythtv-database (0.20-0) ...
Failed to connect to database: Can't connect to MySQL server on '192.168.0.55' (113) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
If you supplied incorrect information, try:
dpkg-reconfigure --force mythtv-database
dpkg: error processing mythtv-database (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mythtv-database
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

The catch here, is that the IP it gives for the MySQL server is the *old* server, not the current machine.  I've edited /etc/mysql/my.cnf, /etc/mythtv/mysql.txt, and ~/.mythtv/mysql.txt but nothing seems to be helping.  Also tweaked the address in myth-setup, but still no luck.  Any ideas?

---

