---
title: "Ubuntu Software Center cannot Install: Package Operations Failed"
date: 2016-04-17
forum: General Help
---

### Post by Nahua_Kang on 2016-04-17
Hi, as LibreOffice Impress does not work, I cleaned up Libre Office and installed OpenOffice.

Today, as I am trying to add German and Chinese to the keyboard, I ran into some issues below. It seems that it has to do with LibreOffice, but I don't know how to fix it so I can install other apps on Ubuntu. Please let me know if any of you can help. Many many thanks!

_**##Update 1**_:  followed ian_weisser's instruction in: [http://ubuntuforums.org/showthread.php?t=2248157](http://ubuntuforums.org/showthread.php?t=2248157)

```

sudo apt-get autoremove libreoffice libreoffice-common
sudo apt-get autoremove libreoffice-core libreoffice-ogltrans
sudo apt-get autoremove libreoffice libreoffice-common libreoffice-core libreoffice-ogltrans libreoffice-base-core libreoffice-math libreoffice-style-galaxy libreoffice-style-human libreoffice-writer python3-uno
sudo apt-get update
sudo apt-get upgrade

```

Seems to solve the issue now and I can install new packages.

> 
nstallArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 203541 files and directories currently installed.)
Preparing to unpack .../libreoffice-common_1%3a5.1.2~rc2-0ubuntu1~trusty0_all.deb ...
Unpacking libreoffice-common (1:5.1.2~rc2-0ubuntu1~trusty0) ...
dpkg: error processing archive /var/cache/apt/archives/libreoffice-common_1%3a5.1.2~rc2-0ubuntu1~trusty0_all.deb (--unpack):
 trying to overwrite '/usr/bin/soffice', which is also in package openoffice-debian-menus 4.1.2-9782
rmdir: failed to remove /var/lib/libreoffice/share/prereg/: No such file or directory
rmdir: failed to remove /var/lib/libreoffice/share/: No such file or directory
rmdir: failed to remove /var/lib/libreoffice/program/: No such file or directory
rmdir: failed to remove /var/lib/libreoffice: No such file or directory
rmdir: failed to remove /var/lib/libreoffice: No such file or directory
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Processing triggers for gnome-icon-theme (3.10.0-0ubuntu2) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Error in function: 
dpkg: dependency problems prevent configuration of libreoffice-style-human:
 libreoffice-style-human depends on libreoffice-common; however:
  Package libreoffice-common is not installed.


dpkg: error processing package libreoffice-style-human (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-style-galaxy:
 libreoffice-style-galaxy depends on libreoffice-common; however:
  Package libreoffice-common is not installed.


dpkg: error processing package libreoffice-style-galaxy (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-core:
 libreoffice-core depends on libreoffice-common (>> 1:5.1.2~rc2); however:
  Package libreoffice-common is not installed.


dpkg: error processing package libreoffice-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-uno:
 python3-uno depends on libreoffice-core (= 1:5.1.2~rc2-0ubuntu1~trusty0); however:
  Package libreoffice-core is not configured yet.




---

### Post by ajgreeny on 2016-04-17
Please mark as SOLVED from the Thread Tools menu at the top.

---

