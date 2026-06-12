---
title: "Package error. How do I fix this problem?"
date: 2012-12-24
forum: General Help
---

### Post by Welly Wu on 2012-12-24
wellywu@System76:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 plasma-widget-message-indicator : Depends: libstdc++6 (>= 421.1) but 4.6.3-1ubuntu5 is installed
E: Unmet dependencies. Try using -f.
wellywu@System76:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  plasma-widget-message-indicator
The following packages will be upgraded:
  plasma-widget-message-indicator
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0 B/37.2 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 16501 package 'plasma-widget-message-indicator':
 missing description
dpkg: error: parsing file '/var/lib/dpkg/available' near line 11719:
 invalid package name (character `' not allowed (only letters, digits and characters `-+._'))
E: Sub-process /usr/bin/dpkg returned an error code (2)
wellywu@System76:~$

---

### Post by Welly Wu on 2012-12-24
[http://askubuntu.com/questions/55099/dpkg-error-parsing-file-var-lib-dpkg-available-near-line-0](http://askubuntu.com/questions/55099/dpkg-error-parsing-file-var-lib-dpkg-available-near-line-0)

sudo apt-get --clear-avail
sudo apt-get update

Solved!

---

