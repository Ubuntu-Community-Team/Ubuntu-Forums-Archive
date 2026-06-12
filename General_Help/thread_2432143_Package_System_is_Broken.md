---
title: "Package System is Broken"
date: 2019-11-27
forum: General Help
---

### Post by geomcd1949 on 2019-11-27
Software Updater says "The package system is broken."

```
Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f
Transaction failed: The package system is broken
 The following packages have unmet dependencies:

libnvidia-ifr1-390: Depends: libnvidia-gl-390 but it is not installed
libnvidia-ifr1-390:i386: Depends: libnvidia-gl-390 but it is not installed
nvidia-driver-390: Depends: libnvidia-gl-390 (= 390.129-0ubuntu0~gpu18.04.1) but it is not installed
                   Depends: nvidia-dkms-390 (= 390.129-0ubuntu0~gpu18.04.1) but 390.129-0ubuntu0~gpu18.04.1 is installed
                   Depends: nvidia-kernel-source-390 (= 390.129-0ubuntu0~gpu18.04.1) but 390.129-0ubuntu0~gpu18.04.1 is installed
                   Depends: libnvidia-compute-390 (= 390.129-0ubuntu0~gpu18.04.1) but 390.129-0ubuntu0~gpu18.04.1 is installed
                   Depends: nvidia-compute-utils-390 (= 390.129-0ubuntu0~gpu18.04.1) but 390.129-0ubuntu0~gpu18.04.1 is installed
                   Depends: libnvidia-decode-390 (= 390.129-0ubuntu0~gpu18.04.1) but 390.129-0ubuntu0~gpu18.04.1 is installed
                   Depends: libnvidia-encode-390 (= 390.129-0ubuntu0~gpu18.04.1) but 390.129-0ubuntu0~gpu18.04.1 is installed
                   Depends: nvidia-utils-390 (= 390.129-0ubuntu0~gpu18.04.1) but 390.129-0ubuntu0~gpu18.04.1 is installed
                   Depends: xserver-xorg-video-nvidia-390 (= 390.129-0ubuntu0~gpu18.04.1) but 390.129-0ubuntu0~gpu18.04.1 is installed
                   Depends: libnvidia-cfg1-390 (= 390.129-0ubuntu0~gpu18.04.1) but 390.129-0ubuntu0~gpu18.04.1 is installed
                   Depends: libnvidia-ifr1-390 (= 390.129-0ubuntu0~gpu18.04.1) but 390.129-0ubuntu0~gpu18.04.1 is installed
                   Depends: libnvidia-fbc1-390 (= 390.129-0ubuntu0~gpu18.04.1) but 390.129-0ubuntu0~gpu18.04.1 is installed
```

Third-party repositories are disabled.

sudo apt-get install -f gives:

```
 sudo apt-get install -f
[sudo] password for george: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  lib32gcc1 libc6-i386 libfdk-aac1 libluajit-5.1-2 libluajit-5.1-common libmbedcrypto1
  libmbedtls10 libmbedx509-0 libnvidia-common-435
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libnvidia-gl-390 libnvidia-gl-390:i386
The following NEW packages will be installed:
  libnvidia-gl-390 libnvidia-gl-390:i386
0 upgraded, 2 newly installed, 0 to remove and 31 not upgraded.
3 not fully installed or removed.
Need to get 0 B/29.2 MB of archives.
After this operation, 147 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 556496 files and directories currently installed.)
Preparing to unpack .../libnvidia-gl-390_390.129-0ubuntu0~gpu18.04.1_i386.deb ...
diversion of /usr/lib/i386-linux-gnu/libGL.so.1 to /usr/lib/i386-linux-gnu/libGL.so.1.distrib by nvidia-340
dpkg-divert: error: mismatch on package
  when removing 'diversion of /usr/lib/i386-linux-gnu/libGL.so.1 by libnvidia-gl-390'
  found 'diversion of /usr/lib/i386-linux-gnu/libGL.so.1 to /usr/lib/i386-linux-gnu/libGL.so.1.distrib by nvidia-340'
dpkg: error processing archive /var/cache/apt/archives/libnvidia-gl-390_390.129-0ubuntu0~gpu18.04.1_i386.deb (--unpack):
 new libnvidia-gl-390:i386 package pre-installation script subprocess returned error exit status 2
Preparing to unpack .../libnvidia-gl-390_390.129-0ubuntu0~gpu18.04.1_amd64.deb ...
diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340
dpkg-divert: error: mismatch on package
  when removing 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 by libnvidia-gl-390'
  found 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340'
dpkg: error processing archive /var/cache/apt/archives/libnvidia-gl-390_390.129-0ubuntu0~gpu18.04.1_amd64.deb (--unpack):
 new libnvidia-gl-390:amd64 package pre-installation script subprocess returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libnvidia-gl-390_390.129-0ubuntu0~gpu18.04.1_i386.deb
 /var/cache/apt/archives/libnvidia-gl-390_390.129-0ubuntu0~gpu18.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
george@george-desktop:~$ 

```

On startup, keyboard inputs aren't accepted, and have to Ctrl+Alt+F2 to get a  terminal, then install and run startx. Then the keyboard will work.
Ubuntu 18.04.3 LTS on an old Z820 workstation

Thanks for advice.

---

