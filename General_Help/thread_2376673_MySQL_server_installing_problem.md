---
title: "MySQL server installing problem"
date: 2017-11-04
forum: General Help
---

### Post by pb35 on 2017-11-04
Bonjour,
I'm trying to install MySQL server but it seems to have more than one problem. :confused:
Im following:[https://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en/](https://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en/)

I have installed this package:[SIZE=2][ mysql-apt-config_0.8.8-1_all.deb]("https://dev.mysql.com/downloads/repo/apt/") from */etc/mysql/mysql...deb*
I have chosen [/SIZE]the options mysql-5.7, and everything enabled and it finishes without any problem.

Then, *sudo apt-get update*.

Next step, install with MySQL: *sudo apt-get install mysql-server* but gives the following errors:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mysql-server is already the newest version (5.7.20-1ubuntu16.04).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up mysql-common (5.7.20-1ubuntu16.04) ...
update-alternatives: error: alternative path /etc/mysql/my.cnf.fallback doesn't exist
dpkg: error processing package mysql-common (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of mysql-community-client:
 mysql-community-client depends on mysql-common (>= 5.7.20-1ubuntu16.04); however:
  Package mysql-common is not configured yet.
  Version of mysql-common on system, provided by mysql-common:amd64, is <none>.

dpkg: error processing package mysql-community-client (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mysql-client:
 mysql-client depends on mysql-community-client (= 5.7.20-1ubuntu16.04); however:
  Package mysql-community-client is not configured yet.

dpkg: error processing package mysql-client (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    dpkg: dependency problems prevent configuration of mysql-community-server:
 mysql-community-server depends on mysql-common (>= 5.7.20-1ubuntu16.04); however:
  Package mysql-common is not configured yet.
  Version of mysql-common on system, provided by mysql-common:amd64, is <none>.
 mysql-community-server depends on mysql-client (= 5.7.20-1ubuntu16.04); however:
  Package mysql-client is not configured yet.

dpkg: error processing package mysql-community-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-community-server (= 5.7.20-1ubuntu16.04); however:
  Package mysql-community-server is not configured yet.

dpkg: error processing package mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            Errors were encountered while processing:
 mysql-common
 mysql-community-client
 mysql-client
 mysql-community-server
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

The mysql file log stopped recording some hours ago, I dont know why. Its quite long so I cannot clip it.

Thanks in advance.

Pb!

---

### Post by QIII on 2017-11-04
Moved to General Help

---

