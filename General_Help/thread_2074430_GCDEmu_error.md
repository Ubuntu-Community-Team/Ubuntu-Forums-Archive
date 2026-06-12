---
title: "GCDEmu error"
date: 2012-10-21
forum: General Help
---

### Post by checoimg on 2012-10-21
This is the error I'm getting while installing this PPA software package. It checks as installed but the program doesn't work properly.
-----------------------------------------------------------------
zahory@frogui:~$ sudo apt-get install gcdemu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  gcdemu
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0 B/35.8 kB of archives.
After this operation, 304 kB of additional disk space will be used.
Selecting previously unselected package gcdemu.
(Reading database ... 159434 files and directories currently installed.)
Unpacking gcdemu (from .../gcdemu_1.5.0-1ubuntu0~quantal1~ppa3_all.deb) ...
Processing triggers for libglib2.0-0:i386 ...
Processing triggers for libglib2.0-0:amd64 ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Setting up vhba-dkms (20120422-1ubuntu0~quantal1~ppa1) ...
Removing old vhba-20120422 DKMS files...

------------------------------
Deleting module version: 20120422
completely from the DKMS tree.
------------------------------
Done.
Loading new vhba-20120422 DKMS files...
First Installation: checking all kernels...
Building only for 3.5.0-17-generic
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
WARNING: Group 'cdrom' already exists.
FATAL: Module vhba not found.
ERROR: Unable to load module.
dpkg: error processing vhba-dkms (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of cdemu-daemon:
 cdemu-daemon depends on vhba-dkms (>= 20110915); however:
  Package vhba-dkms is not configured yet.

dpkg: error processing cdemu-daemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cdemu-client:No apport report written because the error message indicates its a followup error from a previous failure.

 cdemu-client depends on cdemu-daemon (>= 1.5.0); however:
  Package cdemu-daemon is not configured yet.

dpkg: error processing cdemu-client (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gcdemu:No apport report written because the error message indicates its a followup error from a previous failure.

 gcdemu depends on cdemu-daemon (>= 1.5.0); however:
  Package cdemu-daemon is not configured yet.

dpkg: error processing gcdemu (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 vhba-dkms
 cdemu-daemon
 cdemu-client
 gcdemu
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by mc4man on 2012-10-21
> Building only for 3.5.0-17-generic
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
It' possible this is more fallout from linux-headers-generic not being installed by default on 12.10
(currently linux-headers-3.5.0-17-generic or linux-headers-3.5.0-18-generic from proposed.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1068488](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1068488)

You should purge out all packages from the ppa, then do a restart
```
sudo apt-get purge  vhba-dkms gcdemu
```

After restart 
```
sudo apt-get update && sudo apt-get upgrade
```
```
sudo apt-get install linux-headers-generic
```

Then maybe do another restart & then try to install gcdemu though i'd first start with vhba-dkms, then gcdemu
```
sudo apt-get install vhba-dkms
```
```
sudo apt-get install gcdemu
```

Ex. here
 > sudo apt-get install vhba-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  vhba-dkms
0 upgraded, 1 newly installed, 0 to remove and 125 not upgraded.
Need to get 0 B/10.3 kB of archives.
After this operation, 81.9 kB of additional disk space will be used.
Selecting previously unselected package vhba-dkms.
(Reading database ... 218571 files and directories currently installed.)
Unpacking vhba-dkms (from .../vhba-dkms_20120422-1ubuntu0~quantal1~ppa1_all.deb) ...
Setting up vhba-dkms (20120422-1ubuntu0~quantal1~ppa1) ...
Loading new vhba-20120422 DKMS files...
First Installation: checking all kernels...
Building only for 3.5.0-18-generic
Building initial module for 3.5.0-18-generic
Done.

vhba:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.5.0-18-generic/updates/dkms/

depmod........

DKMS: install completed.
WARNING: Group 'cdrom' already exists.


---

### Post by checoimg on 2012-10-22
Thanks mc4man it worked really fine.

---

