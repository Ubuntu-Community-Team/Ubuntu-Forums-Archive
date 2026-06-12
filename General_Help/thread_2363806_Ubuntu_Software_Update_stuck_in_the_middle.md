---
title: "Ubuntu Software Update stuck in the middle"
date: 2017-06-14
forum: General Help
---

### Post by goran1010jovic on 2017-06-14
This is what I get after "$ sudo apt-get update" and "$ sudo apt-get upgrade" :

```
[private]-Latitude-E6410:[COLOR=#00ff00]~$ sudo apt-get update[/COLOR]
Reading package lists... Done
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/google-chrome-beta.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/google-chrome-beta.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/google-chrome-beta.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/google-chrome-beta.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/google-chrome-beta.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/google-chrome-beta.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
[private]-Latitude-E6410[COLOR=#00ff00]:~$ sudo apt-get upgrade[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  gksu libgksu2-0 libgles1-mesa libpkcs11-helper1 openvpn snap-confine
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Setting up libssl1.0.0:amd64 (1.0.2g-1ubuntu4.8) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package libssl1.0.0:amd64 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up libssl1.0.0:i386 (1.0.2g-1ubuntu4.8) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package libssl1.0.0:i386 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of openssl:
 openssl depends on libssl1.0.0 (>= 1.0.2g); however:
  Package libssl1.0.0:amd64 is not configured yet.


dpkg: error processing package openssl (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Setting up flashplugin-installer (26.0.0.126ubuntu0.16.04.1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package flashplugin-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libssl-dev:amd64:
 libssl-dev:amd64 depends on libssl1.0.0 (= 1.0.2g-1ubuntu4.8); however:
  Package libssl1.0.0:amd64 is not configured yet.


dpkg: error processing package libssl-dev:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Processing triggers for libc-bin (2.23-0ubuntu7) ...
Errors were encountered while processing:
 libssl1.0.0:amd64
 libssl1.0.0:i386
 openssl
 flashplugin-installer
 libssl-dev:amd64
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any help is appreciated... I'm new to Ubuntu and this has been going on for a few days...
Tried restarting my laptop but it doesn't help!

EDIT: Just realized this might not be the correct subforum for asking for help... Damn

---

### Post by kc1di on 2017-06-15
do this in a terminal 
```
sudo dpkg --configure -a
```
if that does not work do this next
```
sudo apt autoclean
```
```
sudo apt clean
```
```
sudo apt update
```
Try upgrade again. 
good luck :)

---

