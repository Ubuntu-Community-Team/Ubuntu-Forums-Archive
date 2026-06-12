---
title: "Issues installing mysql"
date: 2007-10-17
forum: General Help
---

### Post by fearevilleet on 2007-10-17
Hi,

I am trying to install mysql via apt-get, but I am running into issues. When I do apt-get install mysql-server-5.0 this is what I get

```

After unpacking 0B of additional disk space will be used.
Setting up mysql-server-5.0 (5.0.24a-9ubuntu2.1) ...
 * Stopping MySQL database server mysqld
   ...done.
 * Starting MySQL database server mysqld
   ...fail!
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code 
```

When I do sudo dpkg --configure -a I get

```
sudo dpkg --configure -a
Setting up mysql-server-5.0 (5.0.24a-9ubuntu2.1) ...
 * Stopping MySQL database server mysqld
   ...done.
 * Starting MySQL database server mysqld
   ...fail!
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server

```

I also set the bind to IP address in my.cnf to my ip. Is there some kind of configuration I am missing?

---

