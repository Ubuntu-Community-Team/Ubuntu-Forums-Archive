---
title: "Howto remove not fully installed package"
date: 2017-06-18
forum: General Help
---

### Post by zkab on 2017-06-18
I tried to install Dolphin (from software menu) but it stalled after 50% ...then I aborted the installation.
Now it seems that there is a package that is not removed properly.
'sudo apt purge dolphin' removed a bunch of packages but after that I get this ...

```
sudo apt-get update; sudo apt-get dist-upgrade; sudo apt-get autoclean; sudo apt-get autoremove; sudo apt-get clean
Hit:1 http://se.archive.ubuntu.com/ubuntu zesty InRelease
Hit:2 http://se.archive.ubuntu.com/ubuntu zesty-updates InRelease                                                                          
Ign:3 http://dl.google.com/linux/chrome/deb stable InRelease                                                                               
Hit:4 http://se.archive.ubuntu.com/ubuntu zesty-backports InRelease                                                                        
Hit:5 http://dl.google.com/linux/chrome/deb stable Release                                                          
Hit:6 http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu zesty InRelease                                 
Get:7 http://security.ubuntu.com/ubuntu zesty-security InRelease [89,2 kB]                    
Hit:8 http://archive.canonical.com/ubuntu zesty InRelease                                                
Hit:9 http://ppa.launchpad.net/team-xbmc/ppa/ubuntu zesty InRelease                                      
Fetched 89,2 kB in 0s (189 kB/s)                                                     
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 1 040 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://se.archive.ubuntu.com/ubuntu zesty/universe amd64 libkf5i18n-data all 5.31.0-0ubuntu1 [1 040 kB]
Fetched 1 040 kB in 0s (8 521 kB/s)       
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1 040 kB of archives.
After this operation, 0 B of additional disk space will be used.

```

and when I 'dpkg -l libkf5i18n-data' I get this ...

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                          Version             Architecture        Description
+++-=============================-===================-===================-===============================================================
iHR libkf5i18n-data               5.31.0-0ubuntu1     all                 Advanced internationalization framework.

How can I get rid of the not fully installed package ?

---

### Post by zkab on 2017-06-18
I tried to remove 'libkf5i18n-data' but got this ...

```
sudo apt purge libkf5i18n-data
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kwayland-data kwayland-integration libdbusmenu-qt5 libfam0 libgpgmepp6 libkf5archive5 libkf5auth-data libkf5auth5 libkf5codecs-data
  libkf5codecs5 libkf5config-bin libkf5config-data libkf5configcore5 libkf5configgui5 libkf5configwidgets-data libkf5coreaddons-data
  libkf5coreaddons5 libkf5crash5 libkf5dbusaddons-bin libkf5dbusaddons-data libkf5dbusaddons5 libkf5guiaddons5 libkf5iconthemes-data
  libkf5idletime5 libkf5itemviews-data libkf5itemviews5 libkf5notifications-data libkf5notifications5 libkf5service-data libkf5wallet-data
  libkf5waylandclient5 libkf5widgetsaddons-data libkf5widgetsaddons5 libkf5windowsystem-data libkf5windowsystem5 libphonon4qt5-4
  libpolkit-qt5-1-1 libqt5script5 libqt5xml5
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  libkf5configwidgets5* libkf5i18n-data* libkf5i18n5* libkf5iconthemes-bin* libkf5iconthemes5* libkf5service-bin* libkf5service5*
  libkf5wallet-bin* libkf5wallet5* libkwalletbackend5-5*
0 upgraded, 0 newly installed, 10 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 19,2 MB disk space will be freed.
Do you want to continue? [Y/n] 
(Reading database ... 225512 files and directories currently installed.)
Removing libkf5wallet-bin (5.31.0-0ubuntu2) ...
Removing libkf5wallet5:amd64 (5.31.0-0ubuntu2) ...
Removing libkwalletbackend5-5:amd64 (5.31.0-0ubuntu2) ...
Removing libkf5service-bin (5.31.0-0ubuntu1) ...
Removing libkf5service5:amd64 (5.31.0-0ubuntu1) ...
Removing libkf5iconthemes-bin (5.31.0-0ubuntu1) ...
Removing libkf5iconthemes5:amd64 (5.31.0-0ubuntu1) ...
Removing libkf5configwidgets5:amd64 (5.31.0-0ubuntu1) ...
Removing libkf5i18n5:amd64 (5.31.0-0ubuntu1) ...
dpkg: error processing package libkf5i18n-data (--remove):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting a removal
Errors were encountered while processing:
 libkf5i18n-data
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by zkab on 2017-06-18
Problem solved ...
1) sudo apt-get install --reinstall libkf5i18n-data
2) sudo apt-get purge libkf5i18n-data
Done !

---

