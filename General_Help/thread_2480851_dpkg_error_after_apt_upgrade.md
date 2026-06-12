---
title: "dpkg error after apt upgrade"
date: 2022-11-12
forum: General Help
---

### Post by globalkartoffel on 2022-11-12
I'm trying to update my system but I get a dpkg error with several packages.

The errors happen with the following packages:
 linux-firmware
 fwupd
 flash-kernel
 initramfs-tools


My system is a raspberry 3 B+ with Ubuntu 20.04.5 LTS aarch64 installed.



```
David@ubuntu:~$ sudo apt update && sudo apt upgrade
[sudo] password for David: 
Hit:1 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) focal InRelease
Hit:2 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) focal-updates InRelease
Hit:3 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) focal-backports InRelease    
Hit:4 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) focal-security InRelease     
Hit:5 [https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) focal InRelease
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
#
# News about significant security updates, features and services will
# appear here to raise awareness and perhaps tease /r/Linux 
# Use 'pro config set apt_news=false' to hide this and future APT news.
#
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up initramfs-tools (0.136ubuntu6.7) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-firmware (1.187.34) ...
Illegal instruction (core dumped)
dpkg: error processing package linux-firmware (--configure):
 installed linux-firmware package post-installation script subprocess returned error exit status 132
Setting up fwupd (1.7.9-1~20.04.1) ...
fwupd-offline-update.service is a disabled or a static unit not running, not starting it.
fwupd-refresh.service is a disabled or a static unit not running, not starting it.
fwupd.service is a disabled or a static unit not running, not starting it.
Illegal instruction (core dumped)
dpkg: error processing package fwupd (--configure):
 installed fwupd package post-installation script subprocess returned error exit status 132
Setting up flash-kernel (3.103ubuntu1~20.04.4) ...
dpkg: error processing package flash-kernel (--configure):
 installed flash-kernel package post-installation script subprocess returned error exit status 132
Processing triggers for initramfs-tools (0.136ubuntu6.7) ...
Illegal instruction (core dumped)
dpkg: error processing package initramfs-tools (--configure):
 installed initramfs-tools package post-installation script subprocess returned error exit status 132
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-firmware
 fwupd
 flash-kernel
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


I have tried several things 

```
dpgk --configure -a
``` 

```
apt-get install -f

```

also I tried to reinstall it with 
```
dpkg -i --force-overwrite /var/cache/apt/archives/
```

but nothing has helped to fix the error.


I have not yet tried uninstalling and then installing the packages because i am afraid of deleting something bad.


[COLOR=#000000]Thank you in advance![/COLOR]

---

