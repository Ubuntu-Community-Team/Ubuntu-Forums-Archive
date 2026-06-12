---
title: "Inconsistent Package and Dependency Problem"
date: 2014-05-08
forum: General Help
---

### Post by Sky Warden on 2014-05-08
Hey, guys. I'm running on Ubuntu 12.10, and weeks ago, I installed MySQL Workbench and well, it got installed and it works fine now, but there's this dependency package problem which has been bugging me whenever I get a daily update. The same with installing or removing a package. This error will show up, even though the installation or removal seems to be completed just fine.

I feel like solving this once and for all because I don't want to meet any problem in the future. It says that python-support is in an inconsistent state, and that I should fix that first before doing any configuration, which is a trouble because some other packages need python-support to be configured, they said.

Well, I don't know what to do. I've tried to re-install mysql, phpmyadmin, and the workbench too, and it's still there. Anyone can help me?

Log for apt-get upgrade:

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0 B/26.7 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error processing python-support (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
dpkg: dependency problems prevent configuration of python-mysql.connector:
 python-mysql.connector depends on python-support (>= 0.90.0); however:
  Package python-support is not configured yet.


dpkg: error processing python-mysql.connector (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mysql-utilities:
 mysql-utilities depends on python-mysql.connector; however:
  Package python-mysql.connector is not configured yet.


dpkg: error processing mysql-utilities (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mysql-workbench:
 mysql-workbench depends on python-mysql.connector; however:
  Package python-mysql.connector is not configured yet.


dpkg: error processing mysql-workbench (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            No apport report written because MaxReports is reached already
                          Errors were encountered while processing:
 python-support
 python-mysql.connector
 mysql-utilities
 mysql-workbench
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

Let me know if you need more information, and thanks.

---

### Post by Ubi_one_2014 on 2014-05-08
try:
sudo apt-get install --reinstall python-support

---

### Post by Impavidus on 2014-05-08
Ubuntu 12.10 has one week of support left. It would be wise to install Ubuntu 14.04 LTS (or one of its lighter flavours) within a week. If I were you I wouldn't go to great lengths to fix the package manager, but just backup all important files and do a clean install of 14.04.

---

### Post by Sky Warden on 2014-05-09
> **Impavidus said:**
> Ubuntu 12.10 has one week of support left. It would be wise to install Ubuntu 14.04 LTS (or one of its lighter flavours) within a week. If I were you I wouldn't go to great lengths to fix the package manager, but just backup all important files and do a clean install of 14.04.

Well, I guess I will do that. I've been wondering to make a clean install. It will be a lot of pain to backup all these data, though. I heard it's really heavy. I'm still considering whether to move or not.

> **Ubi_one_2014 said:**
> try:
sudo apt-get install --reinstall python-support

I've tried to re-install it. No luck.

---

### Post by ian-weisser on 2014-05-09
> **Sky Warden said:**
> I've tried to re-install it. No luck.

Error messages from the attempt could be helpful.

Please show us the output from:
```
dpkg --list | grep python-support
```

---

