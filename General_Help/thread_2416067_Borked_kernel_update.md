---
title: "Borked kernel update"
date: 2019-04-04
forum: General Help
---

### Post by kansasnoob on 2019-04-04
For some reason 4.15.0-47-generic failed to install/upgrade properly. I've been going in circles with this for over an hour:

```
lance@DG41RQ:~$ sudo apt update && sudo apt -f install
[sudo] password for lance: 
Hit:1 https://deb.opera.com/opera-stable stable InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu bionic InRelease                     
Get:3 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]   
Get:4 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]    
Get:5 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB] 
Fetched 252 kB in 1s (255 kB/s)                                                
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.15.0-45 linux-headers-4.15.0-45-generic
  linux-image-4.15.0-45-generic linux-modules-4.15.0-45-generic
  linux-modules-extra-4.15.0-45-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-headers-4.15.0-47 linux-modules-extra-4.15.0-47-generic
The following NEW packages will be installed:
  linux-headers-4.15.0-47 linux-modules-extra-4.15.0-47-generic
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0 B/43.7 MB of archives.
After this operation, 248 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 188138 files and directories currently installed.)
Preparing to unpack .../linux-modules-extra-4.15.0-47-generic_4.15.0-47.50_amd64.deb ...
Unpacking linux-modules-extra-4.15.0-47-generic (4.15.0-47.50) ...
dpkg-deb (subprocess): decompressing archive member: lzma error: compressed data is corrupt
dpkg-deb: error: <decompress> subprocess returned error exit status 2
dpkg: error processing archive /var/cache/apt/archives/linux-modules-extra-4.15.0-47-generic_4.15.0-47.50_amd64.deb (--unpack):
 cannot copy extracted data for './lib/modules/4.15.0-47-generic/kernel/net/bluetooth/bluetooth.ko' to '/lib/modules/4.15.0-47-generic/kernel/net/bluetooth/bluetooth.ko.dpkg-new': unexpected end of file or stream
Preparing to unpack .../linux-headers-4.15.0-47_4.15.0-47.50_all.deb ...
Unpacking linux-headers-4.15.0-47 (4.15.0-47.50) ...
dpkg-deb (subprocess): decompressing archive member: lzma error: compressed data is corrupt
dpkg-deb: error: <decompress> subprocess returned error exit status 2
dpkg: error processing archive /var/cache/apt/archives/linux-headers-4.15.0-47_4.15.0-47.50_all.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
Errors were encountered while processing:
 /var/cache/apt/archives/linux-modules-extra-4.15.0-47-generic_4.15.0-47.50_amd64.deb
 /var/cache/apt/archives/linux-headers-4.15.0-47_4.15.0-47.50_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Luckily I can still boot 4.15.0-46 :)

dpkg wasn't helpful either but may provide more details:

```
lance@DG41RQ:~$ sudo dpkg --configure -a 
dpkg: dependency problems prevent configuration of linux-headers-4.15.0-47-generic:
 linux-headers-4.15.0-47-generic depends on linux-headers-4.15.0-47; however:
  Package linux-headers-4.15.0-47 is not installed.

dpkg: error processing package linux-headers-4.15.0-47-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-modules-extra-4.15.0-47-generic; however:
  Package linux-modules-extra-4.15.0-47-generic is not installed.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-4.15.0-47-generic; however:
  Package linux-headers-4.15.0-47-generic is not configured yet.

dpkg: error processing package linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 4.15.0.47.49); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-headers-generic (= 4.15.0.47.49); however:
  Package linux-headers-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-4.15.0-47-generic
 linux-image-generic
 linux-headers-generic
 linux-generic

```

Around and around I go:

```
lance@DG41RQ:~$ sudo apt --fix-broken install linux-generic  linux-headers-generic  linux-image-generic  linux-headers-4.15.0-47-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-generic is already the newest version (4.15.0.47.49).
linux-headers-4.15.0-47-generic is already the newest version (4.15.0-47.50).
linux-headers-4.15.0-47-generic set to manually installed.
linux-headers-generic is already the newest version (4.15.0.47.49).
linux-headers-generic set to manually installed.
linux-image-generic is already the newest version (4.15.0.47.49).
linux-image-generic set to manually installed.
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 linux-headers-4.15.0-47-generic : Depends: linux-headers-4.15.0-47 but it is not going to be installed
 linux-image-generic : Depends: linux-modules-extra-4.15.0-47-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

```

---

### Post by kansasnoob on 2019-04-05
Apparently just the .deb(s) for those kernel updates were somehow corrupt. A simple apt-get clean got me back on track.

---

