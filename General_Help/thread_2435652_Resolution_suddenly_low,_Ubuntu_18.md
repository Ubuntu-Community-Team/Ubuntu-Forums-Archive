---
title: "Resolution suddenly low, Ubuntu 18"
date: 2020-01-23
forum: General Help
---

### Post by simon12345645645645 on 2020-01-23
A few weeks ago, I booted up my computer, and suddenly my resolution was lower than usual. I was unable to change it via the settings application. I tried various things with regards to uninstalling, reinstalling nvidia drivers and what not -- not of it worked and I ended up just re-installing everything from scratch. That fixed it... for a few days.

Today, I turned my computer on and once again, the resolution came back down to 1024x768. I'm guessing there is a leprechaun in my computer that keeps secretly changing my resolution. How do I kill it?

My driver is nvidia-390, and I have a GeForce GTX 550 Ti.

---

### Post by simon12345645645645 on 2020-01-23
I don't know if it's related, but my package system is current broken:

$ sudo apt --fix-broken install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  libllvm7
Use 'sudo apt autoremove' to remove it.
The following additional packages will be installed:
  libnvidia-gl-390 libnvidia-gl-390:i386
The following NEW packages will be installed:
  libnvidia-gl-390 libnvidia-gl-390:i386
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 29.2 MB of archives.
After this operation, 147 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/restricted i386 libnvidia-gl-390 i386 390.116-0ubuntu0.18.04.1 [14.9 MB]
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/restricted amd64 libnvidia-gl-390 amd64 390.116-0ubuntu0.18.04.1 [14.3 MB]
Fetched 29.2 MB in 2s (13.9 MB/s)            
(Reading database ... 166430 files and directories currently installed.)
Preparing to unpack .../libnvidia-gl-390_390.116-0ubuntu0.18.04.1_i386.deb ...
diversion of /usr/lib/i386-linux-gnu/libGL.so.1 to /usr/lib/i386-linux-gnu/libGL.so.1.distrib by nvidia-340
dpkg-divert: error: mismatch on package
  when removing 'diversion of /usr/lib/i386-linux-gnu/libGL.so.1 by libnvidia-gl-390'
  found 'diversion of /usr/lib/i386-linux-gnu/libGL.so.1 to /usr/lib/i386-linux-gnu/libGL.so.1.distrib by nvidia-340'
dpkg: error processing archive /var/cache/apt/archives/libnvidia-gl-390_390.116-0ubuntu0.18.04.1_i386.deb (--unpack):
 new libnvidia-gl-390:i386 package pre-installation script subprocess returned error exit status 2
Preparing to unpack .../libnvidia-gl-390_390.116-0ubuntu0.18.04.1_amd64.deb ...
diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340
dpkg-divert: error: mismatch on package
  when removing 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 by libnvidia-gl-390'
  found 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340'
dpkg: error processing archive /var/cache/apt/archives/libnvidia-gl-390_390.116-0ubuntu0.18.04.1_amd64.deb (--unpack):
 new libnvidia-gl-390:amd64 package pre-installation script subprocess returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libnvidia-gl-390_390.116-0ubuntu0.18.04.1_i386.deb
 /var/cache/apt/archives/libnvidia-gl-390_390.116-0ubuntu0.18.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by CatKiller on 2020-01-23
The presence of the 340 branch is preventing the 390 branch from installing properly. You should purge all the nvidia stuff and then only install one branch.

---

### Post by simon12345645645645 on 2020-01-23
I seem to have fixed the problem. 

First, I copy pasted a magical incantation from the interwebs to solve my broken package system, then I did:

$ sudo apt update
$ sudo apt upgrade

and, as per the suggestion from the output of sudo apt upgrade:

$ sudo apt autoremove

I rebooted, and abracadabra everything was back to normal.

---

### Post by simon12345645645645 on 2020-01-23
For those who may be wondering, the magical incantation that fixed my broken package system was:

```
sudo su 
for FILE in $(dpkg-divert --list | grep nvidia-340 | awk '{print $3}'); do dpkg-divert --remove $FILE; done
exit


```

---

