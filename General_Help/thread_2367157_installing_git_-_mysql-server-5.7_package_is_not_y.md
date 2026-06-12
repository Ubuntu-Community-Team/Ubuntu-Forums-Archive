---
title: "installing git - mysql-server-5.7 package is not yet configured"
date: 2017-07-26
forum: General Help
---

### Post by marchello_lippi2 on 2017-07-26
Hi all, 

Trying to install git on my ubuntu machine, can not due to dependencies. 

```

(translated by me from my local language into English)
$ sudo apt install git
Reading packages list... Done
Building dependencies tree
Reading information about state... Done
git is already new version (1:2.7.4-0ubuntu1.1).
Packages below were installed automatically and not needed anymore:
  flightgear-data-ai flightgear-data-aircrafts flightgear-data-all flightgear-data-base flightgear-data-models libcoin80v5 libgraphicsmagick-q16-3 libhtsengine1 libjs-excanvas libjs-jquery-flot libjs-jquery-ui libjs-jquery-ui-theme-smoothness
  libjs-leaflet libjs-requirejs libjs-requirejs-text libmircommon5 libopenscenegraph100v5 libopenthreads20 libsimgearcore2017.1.2 libsimgearscene2017.1.2 libudns0 libxine2 libxine2-bin libxine2-doc libxine2-ffmpeg libxine2-misc-plugins
  libxine2-plugins linux-headers-4.4.0-79 linux-headers-4.4.0-79-generic linux-headers-4.4.0-81 linux-headers-4.4.0-81-generic linux-image-4.4.0-79-generic linux-image-4.4.0-81-generic linux-image-extra-4.4.0-79-generic
  linux-image-extra-4.4.0-81-generic
Use 'sudo apt autoremove' to remove them.
updated 0, installed 0 new, 0 marked for deleting and 17 not updated.
not installed(deleted) till the end 2 packages.
After this operation used disk space will be increased for 0 B.
Continue? [Y/n] Y
Configuring mysql-server-5.7 (5.7.19-0ubuntu0.16.04.1) ...
insserv: warning: current start runlevel(s) (empty) of script `mysql' overrides LSB defaults (2 3 4 5).
insserv: warning: current stop runlevel(s) (0 1 2 3 4 5 6) of script `mysql' overrides LSB defaults (0 1 6).
mysql_upgrade: Got error: 2002: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) while connecting to the MySQL server
Upgrade process encountered error and will not continue.
mysql_upgrade failed with exit status 11
dpkg: error processing package mysql-server-5.7 (--configure):
 subprocess installed post-installation scenario returned status error 1
dpkg: packages dependencies do not allow to configure package mysql-server:
 mysql-server depends on mysql-server-5.7; but:
  Package mysql-server-5.7 is not yet configured.


dpkg: error processing package mysql-server (--configure):
 dependencies problem - remains not configured 
Report apport was not recorded, because message about error reveals that this error is because of previous failure.
Got error during processing of packages:                                                                                                                           
 mysql-server-5.7
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

```

$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:        16.04
Codename:       xenial

```

I am able to connect to local mysql server using MySQL WorkBench. 

Please advise.

---

