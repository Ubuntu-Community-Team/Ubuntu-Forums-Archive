---
title: "Can not remove MariaDB to reinstall it after 14.04-18.04 upgrade"
date: 2019-03-04
forum: General Help
---

### Post by eriksson252 on 2019-03-04
Hi all

Upgraded my server from 14.04 to 16.04 and then to 18.04 this weekend. After some problem everythings looked fine. Untill I tried phpmyadmin and everything boggered up....

I right now sit in a JAM. I need to reinstall MariaDB to be able to reinstall phpmyadmin and mysql.
But I amunable to. Anything I try to install gives me

```
You might want to run 'apt --fix-broken install' to correct these.The following packages have unmet dependencies:
 dbconfig-mysql : Depends: default-mysql-client or
                           virtual-mysql-client
 mariadb-server-10.3 : Depends: mariadb-client-10.3 (>= 1:10.3.11+maria~trusty) but it is not installable
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).



```

If I try to run apt --fix-broken install

I just get
```
Reading package lists... DoneBuilding dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  galera-3 libdbi-perl libnet-daemon-perl socat
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  default-mysql-client mysql-client-5.7
The following packages will be REMOVED:
  mariadb-server-10.3
The following NEW packages will be installed:
  default-mysql-client mysql-client-5.7
0 upgraded, 2 newly installed, 1 to remove and 302 not upgraded.
Need to get 0 B/2&#8239;368 kB of archives.
After this operation, 38,4 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 192656 files and directories currently installed.)
Removing mariadb-server-10.3 (1:10.3.11+maria~trusty) ...
Failed to stop mysql.service: Unit mysql.service not loaded.
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: error processing package mariadb-server-10.3 (--remove):
 installed mariadb-server-10.3 package pre-removal script subprocess returned error exit status 5
Errors were encountered while processing:
 mariadb-server-10.3
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

So the main problem is, I can not stop mysql since the service in not installed. But I can not install it, since it hits the wall on dependecies. Have tried everything I can come up with.... Any idees?

---

### Post by TheFu on 2019-03-04
Apache options and config files have drastically changed over those releases.  Check that, if you haven't already.
Same for php settings. Very different. Check those.

I haven't used mysql in along time. We switched to mariadb everything that wouldn't go to postgresql.  I don't remember major issues, except the DB formats changing and some conversions were needed to support specific UTF8 data.

We've never used phpmyadmin. Our security guys think it is a wide open attack vector and don't allow it. Even failed to get it approved using an ssh-tunnel with localhost-only access.

There is a metapackage, I think, that allows either mariadb OR mysql to be used to meet dependency requirements.  At this point, might be easier to flush the box and do a fresh 18.04 install.  I'd test everything on a VM first to ensure I was ready before touching production.

---

