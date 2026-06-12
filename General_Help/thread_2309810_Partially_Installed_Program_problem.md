---
title: "Partially Installed Program problem"
date: 2016-01-13
forum: General Help
---

### Post by Geoff_Lane on 2016-01-13
I have webmin installed on a number of Ubuntu machines including two on Raspberry Pi devices, one running Ubuntu Mate and the other Debian.

I have remote access (via ssh) to a relative's R-Pi and am having major problems with webmin.

Tried installing using Gdebi, system hung, tried again, left it overnight. Not installed.

Tried again using apt-get with webmin repository, again hung on unpacking.

Tried apt-get install, dpkg install, synaptic, no info returned.

Decided to try and remove (purge), get a message saying installation has serious problems and reinstall before trying removal.

I would LOVE to install but can't seem to, second option would LOVE to remove but can't seem to.

Here is my output from two command line instructions;

```
claudia@PiggyPi:~$ sudo apt-get --purge remove webmin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package webmin needs to be reinstalled, but I can't find an archive for it.
claudia@PiggyPi:~$ sudo nano /etc/apt/sources.list
claudia@PiggyPi:~$ sudo apt-get --purge remove webmin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package webmin needs to be reinstalled, but I can't find an archive for it.
claudia@PiggyPi:~$ sudo nano /etc/apt/sources.list
claudia@PiggyPi:~$ sudo dpkg -P webmin
dpkg: error processing package webmin (--purge):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting a removal
Errors were encountered while processing:
 webmin


```

Otherwise R-Pi seems to be working fine but I'd like to remove webmin if I can't install, any advice appreciated.

I have done the normal sudo apt-get update, upgrade etc, all to no avail

Geffers

---

