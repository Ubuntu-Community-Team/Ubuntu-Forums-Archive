---
title: "runit E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2015-07-31
forum: General Help
---

### Post by jiapei100 on 2015-07-31
Hello, all:

I'm using Ubuntu 15.04. whenever I tried to install any package, I got the error message as the title. How can I get rid of this annoying error message????


```
:~$ uname -a
Linux LongerVision001 3.19.0-25-generic #26-Ubuntu SMP Fri Jul 24 21:17:31 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 15.04
Release:        15.04
Codename:       vivid
```



```
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up runit (2.1.2-3ubuntu1) ...
start: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
dpkg: error processing package runit (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 runit
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


Cheers
Pei

---

### Post by slickymaster on 2015-07-31
Try first to remove any local package files laying around, remove obsolete package files that might be left on your system and fix broken dependencies within your package file```
sudo apt-get clean 
sudo apt-get autoclean 
sudo apt-get -f install
```If that doesn't work, try to configure any and all existing unpacked and unconfigured packages running```
sudo dpkg --configure -a
```

---

