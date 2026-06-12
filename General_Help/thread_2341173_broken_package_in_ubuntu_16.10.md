---
title: "broken package in ubuntu 16.10"
date: 2016-10-25
forum: General Help
---

### Post by hunterkasy on 2016-10-25
I try to update my system using the software updater, it says I have broken packages and to use  sudo apt-get install -f command to fix it, this is what happens when I try the command

> tyler@tyler-quad4:~$ sudo apt-get install -f
[sudo] password for tyler: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libboost-signals1.61.0 libmikmod3 libsdl-mixer1.2 linux-headers-4.8.0-21
  linux-headers-4.8.0-21-generic linux-image-4.4.0-38-generic
  linux-image-4.8.0-21-generic linux-image-extra-4.4.0-38-generic
  linux-image-extra-4.8.0-21-generic pingus-data python3-pexpect python3-pil
  python3-ptyprocess python3-renderpm python3-reportlab
  python3-reportlab-accel
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libperl5.22:i386
The following NEW packages will be installed:
  libperl5.22:i386
0 upgraded, 1 newly installed, 0 to remove and 29 not upgraded.
3 not fully installed or removed.
Need to get 0 B/3,028 kB of archives.
After this operation, 15.5 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 300525 files and directories currently installed.)
Preparing to unpack .../libperl5.22_5.22.2-3_i386.deb ...
Unpacking libperl5.22:i386 (5.22.2-3) ...
dpkg: error processing archive /var/cache/apt/archives/libperl5.22_5.22.2-3_i386.deb (--unpack):
 trying to overwrite shared '/usr/share/doc/libperl5.22/changelog.Debian.gz', which is different from other instances of package libperl5.22:i386
Errors were encountered while processing:
 /var/cache/apt/archives/libperl5.22_5.22.2-3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
tyler@tyler-quad4:~$ 


---

