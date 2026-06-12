---
title: "Checking For Updates Will Not Load"
date: 2017-06-07
forum: General Help
---

### Post by wbee on 2017-06-07
Hello,

I'm using 16.04 64b(lts),the version with the Gnome Desktop.

When I open Software Updater,it brings up the checker labeled,"Checking for Updates", but it will not load.

I'm tempted to remove and reinstall it but am afraid I might accidentally erase things needed elsewhere.

Solutions?

-----

Thank you.

---

### Post by Impavidus on 2017-06-07
Try to get some more details by attempting the update from the terminal.```
sudo apt update
sudo apt upgrade
```

---

### Post by wbee on 2017-06-07
```
bee@wbee-A780L3C:~$ sudo apt update
[sudo] password for wbee: 
Sorry, try again.
[sudo] password for wbee: 
Sorry, try again.
[sudo] password for wbee: 
Hit:1 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Get:2 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]    
Hit:3 http://repository.spotify.com stable InRelease                           
Get:4 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]     
Get:5 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]  
Get:6 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [54.6 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [552 kB]
Get:8 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [50.7 kB]
Get:9 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [35.2 kB]
Get:10 http://security.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [46.7 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [536 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [298 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [201 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [162 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [203 kB]
Get:16 http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [2,520 B]
Get:17 http://us.archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11 Metadata [3,328 B]
Get:18 http://us.archive.ubuntu.com/ubuntu xenial-backports/universe amd64 DEP-11 Metadata [3,976 B]
Fetched 2,456 kB in 16s (145 kB/s)                                             
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
wbee@wbee-A780L3C:~$ sudo apt update
Hit:1 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease             
Hit:3 http://repository.spotify.com stable InRelease                           
Hit:4 http://security.ubuntu.com/ubuntu xenial-security InRelease       
Hit:5 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease    
Reading package lists... Done                     
Building dependency tree       
Reading state information... Done
All packages are up to date.
wbee@wbee-A780L3C:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Setting up phonon:amd64 (4:4.8.3-0ubuntu3) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package phonon:amd64 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of kde-runtime:
 kde-runtime depends on phonon; however:
  Package phonon:amd64 is not configured yet.

dpkg: error processing package kde-runtime (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkcompactdisc4:
 libkcompactdisc4 depends on phonon; however:
  Package phonon:amd64 is not configured yet.

dpkg: error processing package libkcompactdisc4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkcddb4:
 libkcddb4 depends on libkcompactdisc4; however:
  Package libkcompactdisc4 is not configured yet.

dpkg: error processing package libkcddb4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libk3b6:
 libk3b6 depends on libkcddb4 (>= 4:4.3.4); however:
  Package libkcddb4 is not configured yet.

dpkg: error processing package libk3b6 (--configure):
 depeNo apport report written because the error message indicates its a followup error from a previous failure.
                               No apport report written because the error message indicates its a followup error from a previous failure.
                                                         No apport report written because MaxReports is reached already
                                       No apport report written because MaxReports is reached already
                     No apport report written because MaxReports is reached already
   No apport report written because MaxReports is reached already
                                                                 ndency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of k3b:
 k3b depends on kde-runtime (>> 4:4.10); however:
  Package kde-runtime is not configured yet.
 k3b depends on libk3b6 (= 2.0.3-0ubuntu5); however:
  Package libk3b6 is not configured yet.
 k3b depends on libkcddb4 (>= 4:4.3.4); however:
  Package libkcddb4 is not configured yet.

dpkg: error processing package k3b (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libk3b6-extracodecs:
 libk3b6-extracodecs depends on libk3b6; however:
  Package libk3b6 is not configured yet.

dpkg: error processing package libk3b6-extracodecs (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 phonon:amd64
 kde-runtime
 libkcompactdisc4
 libkcddb4
 libk3b6
 k3b
 libk3b6-extracodecs
E: Sub-process /usr/bin/dpkg returned an error code (1)
wbee@wbee-A780L3C:~$  
```

---

### Post by wbee on 2017-06-09
For reasons beyond me,it is working now. If it was the result of volunteers working on fixing a bug,thank you.

---

