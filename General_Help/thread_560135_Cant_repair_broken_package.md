---
title: "Cant repair broken package"
date: 2007-09-26
forum: General Help
---

### Post by EYEdROP on 2007-09-26
Im trying to update my system (7.04), and it says a package is brocken and I need to fix it. So I tried, and got this: 
 
ian@PR0BATR0N:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libgle3
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  kde4libs-data
The following NEW packages will be installed:
  kde4libs-data
0 upgraded, 1 newly installed, 0 to remove and 19 not upgraded.
1 not fully installed or removed.
Need to get 0B/7082kB of archives.
After unpacking 28.9MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 209414 files and directories currently installed.)
Unpacking kde4libs-data (from .../kde4libs-data_3.80.3-0ubuntu4_all.deb) ...
Replaced by files in installed package kdelibs5-data ...
dpkg: error processing /var/cache/apt/archives/kde4libs-data_3.80.3-0ubuntu4_all.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/share/apps/kstyle/themes/plastik.themerc', which is also in package kde4base-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kde4libs-data_3.80.3-0ubuntu4_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
ian@PR0BATR0N:~$ 
 
 
Any help?

---

### Post by aonegodman on 2008-01-10
Got same problems. Any ideas to fix the following when trying to fix broken packages:

E: /var/cache/apt/archives/libmjpegtools0_1%3a1.8.0-0.4_i386.deb: trying to overwrite `/usr/lib/libmjpegutils-1.8.so.0.0.0', which is also in package libmjpegtools0c2a


Help! can't update.

---

### Post by iammeagain on 2008-02-02
I tried using synaptic since "apt-get -f install" didnt work. But it wants to remove EVERYother program on the system to reinstall anybroekn  package or package with unmet dependencies

---

