---
title: "Back in Time complete removal"
date: 2018-07-02
forum: General Help
---

### Post by lumaja2 on 2018-07-02
Ubuntu 16.04
 Back in Time 1.2.0
 
 
While trying Back in Time I made two other profiles now I want to remove them, every time I delete they still on main page.
Removed the application with Synaptic check root folder found there still configuration files, in this files must be one with the profiles I want to remove.
Removing with Terminal Terminal cant find the application
```
luis@luis-Ubuntu-16:~$ sudo apt-get remove backintime
[sudo] password for luis: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'backintime' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
luis@luis-Ubuntu-16:~$ sudo apt-get remove back in time
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package back
E: Unable to locate package in [EMAIL="luis@luis-Ubuntu-16"]luis@luis-Ubuntu-16[/EMAIL]:~$
```
 
 
 How can uninstall Bank in Time complete wanting install a clean one.
 Thank you

---

### Post by Frogs Hair on 2018-07-02
Try the following and report back . ```
sudo apt remove backintime-common 
```

---

### Post by lumaja2 on 2018-07-03
After removing Back in Time I reboot the PC checked root folder and there still was configuration files.
Reinstall Back in time found the problem of the two profiles still there and every thing is the same.
The Terminal output:

```
luis@luis-Ubuntu-16:~$ sudo apt remove backintime-common
[sudo] password for luis: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  encfs libboost-serialization1.58.0 librlog5v5 python3-dbus.mainloop.pyqt5
  python3-keyring python3-pyqt5 python3-secretstorage sshfs
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  backintime-common backintime-gnome backintime-qt
0 upgraded, 0 newly installed, 3 to remove and 6 not upgraded.
After this operation, 1,778 kB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 479940 files and directories currently installed.)
Removing backintime-gnome (1.2.0~alpha17~xenial) ...
Removing backintime-qt (1.2.0~alpha17~xenial) ...
Removing backintime-common (1.2.0~alpha17~xenial) ...
Processing triggers for dbus (1.10.6-1ubuntu3.3) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.2) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20180209-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) .................] 
Processing triggers for man-db (2.7.5-1) ...................................] 
luis@luis-Ubuntu-16:~$ sudo apt autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  encfs libboost-serialization1.58.0 librlog5v5
  python3-dbus.mainloop.pyqt5 python3-keyring python3-pyqt5
  python3-secretstorage sshfs
0 upgraded, 0 newly installed, 8 to remove and 6 not upgraded.
After this operation, 16.6 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 479802 files and directories currently installed.)
Removing encfs (1.8.1-3) ...
Removing libboost-serialization1.58.0:i386 (1.58.0+dfsg-5ubuntu3.1) ...
Removing librlog5v5 (1.4-4) ...
Removing python3-dbus.mainloop.pyqt5 (5.5.1+dfsg-3ubuntu4) ...
Removing python3-keyring (7.3-1ubuntu1) ...
Removing python3-pyqt5 (5.5.1+dfsg-3ubuntu4) ...
Removing python3-secretstorage (2.1.3-1) ...
Removing sshfs (2.5-1ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...
luis@luis-Ubuntu-16:~$  
```

---

