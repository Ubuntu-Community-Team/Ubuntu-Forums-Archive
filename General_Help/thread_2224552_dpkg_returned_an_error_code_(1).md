---
title: "dpkg returned an error code (1)"
date: 2014-05-16
forum: General Help
---

### Post by isac630728 on 2014-05-16
Please help. If you tell me to remove the package or re install, will I lose my configs? Idk if remove works or not. I believe it wont. 

```
apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run âapt-get -f installâ to correct these.
The following packages have unmet dependencies.
 mysql-server-5.5 : Depends: mysql-server-core-5.5 (= 5.5.32-0ubuntu0.12.04.1) but 5.5.37-0ubuntu0.12.04.1 is installed
E: Unmet dependencies. Try using -f.

apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  mysql-server mysql-server-5.5
Suggested packages:
  tinyca mailx
The following packages will be upgraded:
  mysql-server mysql-server-5.5
2 upgraded, 0 newly installed, 0 to remove and 109 not upgraded.
2 not fully installed or removed.
Need to get 0 B/8,852 kB of archives.
After this operation, 7,168 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of mysql-server-5.5:
 mysql-server-5.5 depends on mysql-server-core-5.5 (= 5.5.32-0ubuntu0.12.04.1); however:
  Version of mysql-server-core-5.5 on system is 5.5.37-0ubuntu0.12.04.1.
dpkg: error processing mysql-server-5.5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.5; however:
  Package mysql-server-5.5 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
No apport report written because the error message indicates it's a follow-up error from a previous failure.
Errors were encountered while processing:
 mysql-server-5.5
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)





dpkg --configure -a
dpkg: dependency problems prevent configuration of mysql-server-5.5:
 mysql-server-5.5 depends on mysql-server-core-5.5 (= 5.5.32-0ubuntu0.12.04.1); however:
  Version of mysql-server-core-5.5 on system is 5.5.37-0ubuntu0.12.04.1.
dpkg: error processing mysql-server-5.5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.5; however:
  Package mysql-server-5.5 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.5
 mysql-server
```

---

