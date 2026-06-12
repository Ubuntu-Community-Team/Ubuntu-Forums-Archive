---
title: "How can I fix Ubuntu not booting because I stopped the upgrade to 14.04"
date: 2014-04-27
forum: General Help
---

### Post by honglianglu87 on 2014-04-27
I tried to upgrade my computer to Ubuntu 14.04 but when the process come to unpacking firefox-locale. It freezed and wasn't loading, so I waited for about 1.5 hours than I just hard shutdown my computer. After that, I started the computer an chose Ubuntu in GRUB. When PowerTOP 2.4 loaded. I couldn't do anything, it was if the computer locked up. Why?

---

### Post by drac-noc on 2014-04-27
[http://ubuntuforums.org/showthread.php?t=157250](http://ubuntuforums.org/showthread.php?t=157250)

This post might be able to help you.

---

### Post by honglianglu87 on 2014-04-27
> **drac-noc said:**
> [http://ubuntuforums.org/showthread.php?t=157250](http://ubuntuforums.org/showthread.php?t=157250)  This post might be able to help you.  Thanks a lot! But I meet the problems,  
by  apt-get upgrade The output is like the following, and i can not install any packages!  
 
1 upgraded, 0 newly installed, 0 to remove and 23 not upgraded. 
195 not fully installed or removed. 
Need to get 0 B/459 kB of archives. 
After this operation, 828 kB of additional disk space will be used. 
Do you want to continue? [Y/n] y 
(Reading database ... 649946 files and directories currently installed.) 
Preparing to unpack .../modemmanager_1.0.0-2ubuntu1_i386.deb ... 
invoke-rc.d: unknown initscript, /etc/init.d/modemmanager not found. 
dpkg: warning: subprocess old pre-removal script returned error exit status 100 
dpkg: trying script from the new package instead ... 
invoke-rc.d: unknown initscript, /etc/init.d/modemmanager not found. 
dpkg: error processing archive /var/cache/apt/archives/modemmanager_1.0.0-2ubuntu1_i386.deb (--unpack): 
 subprocess new pre-removal script returned error exit status 100 
invoke-rc.d: unknown initscript, /etc/init.d/modemmanager not found. 
dpkg: error while cleaning up: 
 subprocess installed post-installation script returned error exit status 100 
Errors were encountered while processing: 
 /var/cache/apt/archives/modemmanager_1.0.0-2ubuntu1_i386.deb 
Error connecting: Could not connect: Connection refused 
E: Sub-process /usr/bin/dpkg returned an error code (1) 
 
dpkg -a --configure 
 
  dpkg: error processing package modemmanager (--configure): 
 package is in a very bad inconsistent state; you should 
 reinstall it before attempting configuration 
Setting up whoopsie (0.2.24.5) ... 
 
What can i do? Thanks a lot!!

---

### Post by honglianglu87 on 2014-04-28
o my god, I just in the chroot enviroment , touc /etc/init.d/modemmaneger then just apt-get dist-upgrade, it looks like work well......
But there are new problems come up, 
as I rescue the ubuntu with livecd of knoppix, and in a chroot enviroment, the problem is: 
Setting up udev (204-5ubuntu20) ...
 * udev requires devtmpfs support, not started
   ...fail!
invoke-rc.d: initscript udev, action "restart" failed.
dpkg: error processing package udev (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of initramfs-tools:
 How to fix that? Can anyone help me???

---

