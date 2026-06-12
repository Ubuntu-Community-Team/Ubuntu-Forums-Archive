---
title: "Problems installing MYSql"
date: 2007-04-29
forum: General Help
---

### Post by Wesslan on 2007-04-29
I'm using 6.06 server.

I'm following the steps for installing MYSql described at [https://help.ubuntu.com/6.10/ubuntu/serverguide/C/databases.html]("https://help.ubuntu.com/6.10/ubuntu/serverguide/C/databases.html") but it I get the following error message:
invoke-rc.d: unknown initscript, /etc/init.d/mysql not found.

Full log:
```

apt-get install mysql-server mysql-client
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libdbd-mysql-perl libmysqlclient15off mysql-client-5.0 mysql-common mysql-server-5.0
Recommended packages:
  mailx
The following NEW packages will be installed:
  libdbd-mysql-perl libmysqlclient15off mysql-client mysql-client-5.0 mysql-common
  mysql-server mysql-server-5.0
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 29.3MB of archives.
After unpacking 66.8MB of additional disk space will be used.
Do you want to continue [Y/n]?
Get:1 http://se.archive.ubuntu.com dapper/main libdbd-mysql-perl 3.0002-2build1 [139kB]
Get:2 http://security.ubuntu.com dapper-security/main mysql-common 5.0.22-0ubuntu6.06.3 [39.5kB]
Get:3 http://security.ubuntu.com dapper-security/main libmysqlclient15off 5.0.22-0ubuntu6.06.3 [1382kB]
Get:4 http://security.ubuntu.com dapper-security/main mysql-client-5.0 5.0.22-0ubuntu6.06.3 [6278kB]
Get:5 http://security.ubuntu.com dapper-security/main mysql-client 5.0.22-0ubuntu6.06.3 [37.0kB]
Get:6 http://security.ubuntu.com dapper-security/main mysql-server-5.0 5.0.22-0ubuntu6.06.3 [21.3MB]
Get:7 http://security.ubuntu.com dapper-security/main mysql-server 5.0.22-0ubuntu6.06.3 [37.0kB]
Fetched 29.3MB in 25s (1143kB/s)
Preconfiguring packages ...
Selecting previously deselected package mysql-common.
(Reading database ... 33187 files and directories currently installed.)
Unpacking mysql-common (from .../mysql-common_5.0.22-0ubuntu6.06.3_all.deb) ...
Selecting previously deselected package libmysqlclient15off.
Unpacking libmysqlclient15off (from .../libmysqlclient15off_5.0.22-0ubuntu6.06.3_i386.deb) ...
Selecting previously deselected package libdbd-mysql-perl.
Unpacking libdbd-mysql-perl (from .../libdbd-mysql-perl_3.0002-2build1_i386.deb) ...
Selecting previously deselected package mysql-client-5.0.
Unpacking mysql-client-5.0 (from .../mysql-client-5.0_5.0.22-0ubuntu6.06.3_i386.deb) ...
Selecting previously deselected package mysql-client.
Unpacking mysql-client (from .../mysql-client_5.0.22-0ubuntu6.06.3_all.deb) ...
Selecting previously deselected package mysql-server-5.0.
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.0.22-0ubuntu6.06.3_i386.deb) ...
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.0.22-0ubuntu6.06.3_all.deb) ...
Setting up mysql-common (5.0.22-0ubuntu6.06.3) ...
Setting up libmysqlclient15off (5.0.22-0ubuntu6.06.3) ...

Setting up libdbd-mysql-perl (3.0002-2build1) ...
Setting up mysql-client-5.0 (5.0.22-0ubuntu6.06.3) ...
Setting up mysql-client (5.0.22-0ubuntu6.06.3) ...
Setting up mysql-server-5.0 (5.0.22-0ubuntu6.06.3) ...
invoke-rc.d: unknown initscript, /etc/init.d/mysql not found.

Setting up mysql-server (5.0.22-0ubuntu6.06.3) ...

```

Any ideas?

---

### Post by bamsebv on 2007-06-12
same problem! searched the web but couldn't solve the problem.
using ubuntu 7.04

---

### Post by firebadger on 2007-06-12
Were you root when you ran apt-get?

I notice it wasn't preceeded with a sudo.

---

### Post by bamsebv on 2007-06-12
yes... i was root.. the problem is that after install i can't find /etc/init.d/mysql

---

### Post by gerscht on 2007-06-12
---

---

### Post by firebadger on 2007-06-12
It is called mysql not mysqld.

Might be an idea to remove... using apt-get --purge and then reinstall.

---

