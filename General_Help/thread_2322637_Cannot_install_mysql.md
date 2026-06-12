---
title: "Cannot install mysql"
date: 2016-04-29
forum: General Help
---

### Post by rdh61 on 2016-04-29
Hi,

Lubuntu 16.04 LTS.

Trying to install mysql, I always get the following error:

Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.7_5.7.12-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

See in full below:

```
robert@robert-desktop:~$ sudo apt-get install mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  mysql-client-5.7 mysql-client-core-5.7 mysql-common mysql-server-5.7
  mysql-server-core-5.7
Suggested packages:
  tinyca
The following NEW packages will be installed
  mysql-client-5.7 mysql-client-core-5.7 mysql-common mysql-server
  mysql-server-5.7 mysql-server-core-5.7
0 to upgrade, 6 to newly install, 0 to remove and 0 not to upgrade.
Need to get 18.2 MB of archives.
After this operation, 156 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://es.archive.ubuntu.com/ubuntu xenial-updates/main i386 mysql-common all 5.7.12-0ubuntu1 [17.0 kB]
Get:2 http://es.archive.ubuntu.com/ubuntu xenial-updates/main i386 mysql-client-core-5.7 i386 5.7.12-0ubuntu1 [6,230 kB]
Get:3 http://es.archive.ubuntu.com/ubuntu xenial-updates/main i386 mysql-client-5.7 i386 5.7.12-0ubuntu1 [1,753 kB]
Get:4 http://es.archive.ubuntu.com/ubuntu xenial-updates/main i386 mysql-server-core-5.7 i386 5.7.12-0ubuntu1 [7,616 kB]
Get:5 http://es.archive.ubuntu.com/ubuntu xenial-updates/main i386 mysql-server-5.7 i386 5.7.12-0ubuntu1 [2,558 kB]
Get:6 http://es.archive.ubuntu.com/ubuntu xenial-updates/main i386 mysql-server all 5.7.12-0ubuntu1 [10.1 kB]
Fetched 18.2 MB in 17s (1,014 kB/s)                                            
Preconfiguring packages ...
Selecting previously unselected package mysql-common.
(Reading database ... 251386 files and directories currently installed.)
Preparing to unpack .../mysql-common_5.7.12-0ubuntu1_all.deb ...
Unpacking mysql-common (5.7.12-0ubuntu1) ...
Selecting previously unselected package mysql-client-core-5.7.
Preparing to unpack .../mysql-client-core-5.7_5.7.12-0ubuntu1_i386.deb ...
Unpacking mysql-client-core-5.7 (5.7.12-0ubuntu1) ...
Selecting previously unselected package mysql-client-5.7.
Preparing to unpack .../mysql-client-5.7_5.7.12-0ubuntu1_i386.deb ...
Unpacking mysql-client-5.7 (5.7.12-0ubuntu1) ...
Selecting previously unselected package mysql-server-core-5.7.
Preparing to unpack .../mysql-server-core-5.7_5.7.12-0ubuntu1_i386.deb ...
Unpacking mysql-server-core-5.7 (5.7.12-0ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up mysql-common (5.7.12-0ubuntu1) ...
update-alternatives: using /etc/mysql/my.cnf.fallback to provide /etc/mysql/my.cnf (my.cnf) in auto mode
(Reading database ... 251542 files and directories currently installed.)
Preparing to unpack .../mysql-server-5.7_5.7.12-0ubuntu1_i386.deb ...
Aborting downgrade from (at least) 10.0 to 5.7.
If are sure you want to downgrade to 5.7, remove the file
/var/lib/mysql/debian-*.flag and try installing again.
dpkg: error processing archive /var/cache/apt/archives/mysql-server-5.7_5.7.12-0ubuntu1_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Selecting previously unselected package mysql-server.
Preparing to unpack .../mysql-server_5.7.12-0ubuntu1_all.deb ...
Unpacking mysql-server (5.7.12-0ubuntu1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.7_5.7.12-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
robert@robert-desktop:~$
```

Can somebody please help me sort this?

Many thanks.

---

### Post by T.J. on 2016-04-30
> **rdh61 said:**
> 
.
Aborting downgrade from (at least) 10.0 to 5.7.
If are sure you want to downgrade to 5.7, remove the file
/var/lib/mysql/debian-*.flag and try installing again.


Remove the /var/lib/mysql/debian-*.flag files, otherwise it will remain blocked.  Whoever packaged mysql was a little sloppy in my opinion.

---

### Post by rdh61 on 2016-05-02
Thanks for your answer. I was confused by the offer to downgrade - as far as I am concerned 10.0 was not installed. I resolved this issue before your reply by doing the following:

1. [Completely removing mysql]("http://stackoverflow.com/questions/25244606/completely-remove-mysql-ubuntu-14-04-lts"). This would only work if I removed mysql-client and mysql-common before mysql-server.
2. Rebooting.
3. sudo apt-get install mysql-server-5.7  - Note: if I didn't specify 5.7 I got the same result as before.

---

