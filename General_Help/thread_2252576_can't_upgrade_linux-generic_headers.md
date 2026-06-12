---
title: "can't upgrade linux-generic headers"
date: 2014-11-12
forum: General Help
---

### Post by jd6 on 2014-11-12
I've searched the interwebs high and low tried lots of different thing still always come back to this error. I cant install or upgrade anything without the linux-headers error being thrown. 

Anyone have any insight?

Thanks in advance!

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-common is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-generic : Depends: linux-image-generic (= 3.2.0.69.82) but 3.2.0.70.84 is to be installed
                 Depends: linux-headers-generic (= 3.2.0.69.82) but 3.2.0.70.84 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
jd@server:/$ 

```

apt-get -f install output 

```
jd@server:/$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-generic
The following packages will be upgraded:
  linux-generic
1 upgraded, 0 newly installed, 0 to remove and 76 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1,716 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.69.82); however:
  Version of linux-image-generic on system is 3.2.0.70.84.
 linux-generic depends on linux-headers-generic (= 3.2.0.69.82); however:
  Version of linux-headers-generic on system is 3.2.0.70.84.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
jd@server:/$ 

```

---

### Post by Impavidus on 2014-11-13
Your linux-image-generic and linux-headers-generic are at version 3.2.0.70, but your linux-generic is at the outdated version 3.2.0.69. As linux-generic is an empty metapackage, you should be able to remove it without real consequences and then install the latest version.```
sudo dpkg -r linux-generic
sudo apt-get update
sudo apt-get install linux-generic
```

---

