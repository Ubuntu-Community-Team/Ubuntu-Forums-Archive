---
title: "Apt-get error.. How do I reinstall it?"
date: 2005-10-17
forum: General Help
---

### Post by zoulman on 2005-10-17
Hi everyone,

I messed up my apt installation by deleting everything in /var/cache/apt/archives/. douh.. I know. Well I can't seem to figure out how to reinstall APT-GET to get it working again.

Any ideas? :confused: 

Thanks

---

### Post by plumcreek on 2005-10-17
[quote=zoulman]I messed up my apt installation by deleting everything in /var/cache/apt/archives/. douh.. I know. Well I can't seem to figure out how to reinstall APT-GET to get it working again.[/quote] 
The following installation instructions should work if dpkg is still working.

First, open up your terminal.

Next, download the .deb file:
```
wget http://archive.ubuntulinux.org/ubuntu/pool/main/a/apt/apt_0.6.40.1ubuntu9_i386.deb
``` 
Now install the .deb file with dpkg:
```
sudo dpkg -i apt_0.6.40.1ubuntu9_i386.deb
``` 
That should get apt installed and hopefully get it working again.

---

