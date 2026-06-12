---
title: "Remastersys fail?"
date: 2014-03-03
forum: General Help
---

### Post by einstein**-7 on 2014-03-03
I'm tring to create a clone of my current system with remastersys and eventually a backup but it fails.  
Here are the only errors in the log file.. 

```
Cannot stat source directory "/Net" because No such file or directory
##############
Removing the ubiquity frontend as it has been included and is not needed on the normal system
Calculating the installed filesystem size for the installer
Removing remastersys-firstboot from system startup
The filesystem.squashfs filesystem is missing.  Either there was a problem creating the compressed filesystem or you are trying to run sudo remastersys dist iso before sudo remastersys dist cdfs
```

Any ideas??

---

### Post by phidia on 2014-03-03
Does the filesystem include an NTFS? If so you could [read this]("http://forums.linuxmint.com/viewtopic.php?t=141555&p=749318"). 
I'm not sure that is totally applicable but the poster there did get a version of remastersys to go through it's process without erring out.

---

