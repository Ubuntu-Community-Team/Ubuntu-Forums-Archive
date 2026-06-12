---
title: "The package system is broken"
date: 2013-05-31
forum: General Help
---

### Post by SeppKm on 2013-05-31
Hi there,

my package system is broken. If i want to "Install Updates" (Complete Generic Linux Kernel. Changes for the versions: Installed version: 3.2.0.41.49. Available version: 3.2.0.44.53) via Update Manager I get following error message: "The package system is broken. Check if you are using third party repositories. If so disable them, since they are a common source of problems.Furthermore run the following command in a Terminal: apt-get install -f". Details: "The following packages have unmet dependencies: linux-generic: Depends: linux-image-generic (= 3.2.0.41.49) but 3.2.0.44.53 is installed. Depends: linux-headers-generic (= 3.2.0.41.49) but 3.2.0.44.53 is installed"

Also Ubuntu Software Center is not running with error "Items cannot be installed or removed until the package catalog is repaired". But i cannot repair it get a similar message with linux-generic depends on.

Any ideas?
Thanks a lot.

---

### Post by plucky on 2013-05-31
> **SeppKm said:**
> Hi there,

my package system is broken. If i want to "Install Updates" (Complete Generic Linux Kernel. Changes for the versions: Installed version: 3.2.0.41.49. Available version: 3.2.0.44.53) via Update Manager I get following error message: "The package system is broken. Check if you are using third party repositories. If so disable them, since they are a common source of problems.Furthermore run the following command in a Terminal: apt-get install -f". Details: "The following packages have unmet dependencies: linux-generic: Depends: linux-image-generic (= 3.2.0.41.49) but 3.2.0.44.53 is installed. Depends: linux-headers-generic (= 3.2.0.41.49) but 3.2.0.44.53 is installed"

Also Ubuntu Software Center is not running with error "Items cannot be installed or removed until the package catalog is repaired". But i cannot repair it get a similar message with linux-generic depends on.

Any ideas?
Thanks a lot.


Open a terminal and run ```
sudo apt-get install -f
``` and post the whole output back to the forum.

Post the output between [noparse]```
Your text
```[/noparse] brackets.

Good Luck

---

### Post by SeppKm on 2013-05-31
```
root@zentyal:/home/hias# sudo apt-get install -fReading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done


The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-39-generic adzapper squid3-common linux-headers-3.2.0-38
  linux-headers-3.2.0-39 dansguardian squid3 squid-langpack
  linux-headers-3.2.0-38-generic libgeoip1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-generic
The following packages will be upgraded:
  linux-generic
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1,720 B of archives.
After this operation, 0 B of additional disk space will be used.
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.41.49); however:
  Version of linux-image-generic on system is 3.2.0.45.54.
 linux-generic depends on linux-headers-generic (= 3.2.0.41.49); however:
  Version of linux-headers-generic on system is 3.2.0.45.54.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

