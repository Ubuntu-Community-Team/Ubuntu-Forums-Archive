---
title: "Sub-process /usr/bin/dpkg returned an error code (1).LXDE 18.04"
date: 2018-11-16
forum: General Help
---

### Post by lsjm on 2018-11-16
Dear Friends,

I cannot onstall any application in my computer and I have the following error when I Try sudo apt-get upgrade:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libegl1 libgl1 libgles2 libglvnd-core-dev libglvnd-dev libglvnd0 libglx0
  libopengl0
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
5 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [S/n] s
Setting up grub-pc (2.02-2ubuntu8.7) ...
dpkg: error processing package grub-pc (--configure):
 installed grub-pc package post-installation script subprocess returned error exit status 10
Setting up samba-common (2:4.7.6+dfsg~ubuntu-0ubuntu2.2) ...
dpkg: error processing package samba-common (--configure):
 installed samba-common package post-installation script subprocess returned error exit status 10
Setting up unattended-upgrades (1.1ubuntu1.18.04.6) ...
dpkg: error processing package unattended-upgrades (--configure):
 installed unattended-upgrades package post-installation script subprocess returned error exit status 10
dpkg: dependency problems prevent configuration of samba:
 samba depends on samba-common (= 2:4.7.6+dfsg~ubuntu-0ubuntu2.2); however:
  Package samba-common is not configured yet.

dpkg: error processing package samba (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of samba-common-bin:
 samba-common-bin depends on samba-common (= 2:4.7.6+dfsg~ubuntu-0ubuntu2.2); however:
  Package samba-common is not configured yet.

dpkg: error processing package samba-common-bin (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            Errors were encountered while processing:
 grub-pc
 samba-common
 unattended-upgrades
 samba
 samba-common-bin
```

Any solution please?
Thanks in advance

Luis

---

### Post by deadflowr on 2018-11-16
You have 5 packages that were not properly updated.
Try
```
sudo apt update
sudo apt install -f
```
post back results.

---

### Post by lsjm on 2018-11-17
Hello , unfortunately same result:

```
pepi@pepi-CQ2702ES:~$ sudo apt install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
5 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up grub-pc (2.02-2ubuntu8.7) ...
dpkg: error processing package grub-pc (--configure):
 installed grub-pc package post-installation script subprocess returned error exit status 10
Setting up samba-common (2:4.7.6+dfsg~ubuntu-0ubuntu2.2) ...
dpkg: error processing package samba-common (--configure):
 installed samba-common package post-installation script subprocess returned error exit status 10
Setting up unattended-upgrades (1.1ubuntu1.18.04.6) ...
dpkg: error processing package unattended-upgrades (--configure):
 installed unattended-upgrades package post-installation script subprocess returned error exit status 10
dpkg: dependency problems prevent configuration of samba:
 samba depends on samba-common (= 2:4.7.6+dfsg~ubuntu-0ubuntu2.2); however:
  Package samba-common is not configured yet.

dpkg: error processing package samba (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of samba-common-bin:
 samba-common-bin depends on samba-common (= 2:4.7.6+dfsg~ubuntu-0ubuntu2.2); however:
  Package samba-common is not configured yet.

dpkg: error processing package samba-common-bin (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            Errors were encountered while processing:
 grub-pc
 samba-common
 unattended-upgrades
 samba
 samba-common-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by deadflowr on 2018-11-17
You can follow the methods listed here (other than the one I posted already)
[https://itsfoss.com/dpkg-returned-an-error-code-1/]("https://itsfoss.com/dpkg-returned-an-error-code-1/")

Hopefully the first method of 
```
sudo dpkg --configure -a
```
will work.
If not try the next ones.

I have a feeling it might come to you needing to do a quick remove and reinstall of the listed affected packages.

---

### Post by lsjm on 2018-11-17
Finally I remove the packages and reinstalled so I have no errors.
But as soon as I try to install Samba again I find the same problem

---

