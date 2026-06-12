---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2013-01-26
forum: General Help
---

### Post by Spyderkid on 2013-01-26
I seem to have encountered problems with the software-center, and the general removal, or installation of packages, even through synaptic package manager. And I am often getting system error messages

When I try to sudo apt-get update/upgrade I often get errors, and if I try to re-install the software-center it fails with the error 
[B]"Errors were encountered while processing: /var/cache/apt/archives/software-center_5.2.7_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)"[/B] I am completely stuck on what to do, I've tried sudo apt-get purge software-center and others and none seem to work.

This is the full output of "sudo apt-get install -f software-center"
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  software-center
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/625 kB of archives.
After this operation, 4,395 kB of additional disk space will be used.
(Reading database ... 278736 files and directories currently installed.)
Unpacking software-center (from .../software-center_5.2.7_all.deb) ...
dpkg: error processing /var/cache/apt/archives/software-center_5.2.7_all.deb (--unpack):
 trying to overwrite '/usr/share/app-install/channels', which is also in package app-install-data-partner 12.12.04.1
No apport report written because MaxReports has already been reached
                                                                    Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Errors were encountered while processing:
 /var/cache/apt/archives/software-center_5.2.7_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```I am running ubuntu 12.04 32bit

All Help Appreciated :)

---

### Post by wojox on 2013-01-26
Try these here:
```
sudo dpkg --configure -a
```
```
sudo apt-get install -f
```

---

### Post by Spyderkid on 2013-01-26
I tried them and noticed no difference :/

---

### Post by wojox on 2013-01-26
```
sudo -i
cd /var/cache/apt/archives
dpkg -i --force-overwrite software-center_5.2.7_all.deb
dpkg --configure -a

```

---

### Post by Spyderkid on 2013-01-26
Thanks, that's seemed to sort out the software-center. 

Much appreciated :)

---

### Post by mörgæs on 2013-01-26
Good, then please mark the thread 'solved'.

---

