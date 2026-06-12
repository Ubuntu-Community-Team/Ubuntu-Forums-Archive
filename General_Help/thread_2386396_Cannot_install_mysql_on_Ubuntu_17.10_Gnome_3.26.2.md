---
title: "Cannot install mysql on Ubuntu 17.10 Gnome 3.26.2"
date: 2018-03-05
forum: General Help
---

### Post by prabhat7298 on 2018-03-05
Trying to install mysql, I always get the following error:

Errors were encountered while processing:
/var/cache/apt/archives/mysql-server-5.7_5.7.21-0ubuntu0.17.10.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


See in full below:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  mailx tinyca
The following NEW packages will be installed:
  mysql-server-5.7
0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
Need to get 0 B/3,184 kB of archives.
After this operation, 48.3 MB of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 283762 files and directories currently installed.)
Preparing to unpack .../mysql-server-5.7_5.7.21-0ubuntu0.17.10.1_amd64.deb ...
Failed to stop mysql.service: Unit mysql.service not loaded.
invoke-rc.d: initscript mysql, action "stop" failed.
invoke-rc.d returned 5
There is a MySQL server running, but we failed in our attempts to stop it.
Stop it yourself and try again!
dpkg: error processing archive /var/cache/apt/archives/mysql-server-5.7_5.7.21-0ubuntu0.17.10.1_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.7_5.7.21-0ubuntu0.17.10.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I have tried this solution :
[https://ubuntuforums.org/showthread.php?t=2322637](https://ubuntuforums.org/showthread.php?t=2322637)

Even mysql server is not entirely removed by ```
sudo apt-get remove --purge mysql-server
```
Because it is showing that mysql is not installed. All this is causing broken dependencies and I couldn't even install any other package unless and until I remove mysql-server completely using synaptic manager. Please help I'm very fond of ubuntu 17.10 but now it seems like a real hectic

---

