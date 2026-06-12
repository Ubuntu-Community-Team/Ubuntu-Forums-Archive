---
title: "Error removing phppgadmin"
date: 2007-01-04
forum: General Help
---

### Post by ryanmacleod on 2007-01-04
Hi,


I am running the default ubuntu install. A few months back i successfully installed phppgadmin,

Today I ran the command apt-get install phpmyadmin and everything has stopped working.

I cannot remove phppgadmin anymore, and it has stopped working,

I am trying to do a apt-get upgrade in the hope of fixing things, but it doesn work. Any ideas??

root@KORMA:/home/ryanmacleod# apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED
  phppgadmin
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 4035kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 91176 files and directories currently installed.)
Removing phppgadmin ...
dpkg: error processing phppgadmin (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 phppgadmin
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@KORMA:/home/ryanmacleod#

---

