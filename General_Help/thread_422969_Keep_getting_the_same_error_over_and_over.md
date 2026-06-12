---
title: "Keep getting the same error over and over"
date: 2007-04-25
forum: General Help
---

### Post by brentcee23 on 2007-04-25
Iam a newbie to all of.... Whenever I install or uninstall anything I keep getting this:

E: hplip: subprocess post-installation script returned error exit status 1

Any help on what to do would be greatly appreciated, Thanks!

---

### Post by linuxgeekery on 2007-04-25
try opening a terminal and running "sudo apt-get -f install"

---

### Post by brentcee23 on 2007-04-25
thanks for the quick reply, Here is what happend. any ideas now?

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libapr0 libwavpack0 libsvn0 libxine-main1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up hplip (1.7.3-0ubuntu1) ...
Creating/updating hplip user account...
 * Starting HP Linux Printing and Imaging System                         [fail] 
invoke-rc.d: initscript hplip, action "start" failed.
dpkg: error processing hplip (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 hplip
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

