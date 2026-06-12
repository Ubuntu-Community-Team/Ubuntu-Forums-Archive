---
title: "Adobe Flash Plugin Won't Install"
date: 2013-02-10
forum: General Help
---

### Post by clbaines on 2013-02-10
During normal system update an error kept occurring that would not let it complete. The problem was that it could not get a file for the Adobe Flash Plugin Installer. So I removed Adobe Flash. The updates completed. There has to be a glitch in the repository, I think, that will not download flash. I am using Synaptic package manager to reinstall and it can't get by this message:


Preconfiguring packages ...
Selecting previously unselected package flashplugin-installer.
(Reading database ... 610035 files and directories currently installed.)
Unpacking flashplugin-installer (from .../flashplugin-installer_11.2.202.262ubuntu0.12.04.1_i386.deb) ...
Processing triggers for update-notifier-common ...
flashplugin-installer: downloading [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.262.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.262.orig.tar.gz)

Any thoughts on this one?

---

### Post by pqwoerituytrueiwoq on 2013-02-10
```
sudo sed -i 's/\# deb h/deb h/;s/\# deb-src h/deb-src h/' /etc/apt/sources.list;sudo apt-get update;sudo apt-get purge flashplugin-installer;sudo apt-get install adobe-flashplugin adobe-flash-properties-gtk
```
this will enable the Canonical Partners repo, update the apt database, purge flash, and install flash

if you are using kde change gtk at the end of the command to kde

---

### Post by deadflowr on 2013-02-10
> flashplugin-installer: downloading [http://archive.canonical.com/pool/pa...62.orig.tar.gz](http://archive.canonical.com/pool/pa...62.orig.tar.gz)


When it reaches this line, is it just hanging there as if nothing is happening?

If so then it is actually doing its thing and installing it.

I've actually seen it hang at this for something like 4 or 5 minutes, as if it froze. If you wait it out, it might eventually kick back into gear.

---

### Post by clbaines on 2013-02-10
> **pqwoerituytrueiwoq said:**
> ```
sudo sed -i 's/\# deb h/deb h/;s/\# deb-src h/deb-src h/' /etc/apt/sources.list;sudo apt-get update;sudo apt-get purge flashplugin-installer;sudo apt-get install adobe-flashplugin adobe-flash-properties-gtk
```
this will enable the Canonical Partners repo, update the apt database, purge flash, and install flash

if you are using kde change gtk at the end of the command to kde

Thanks for the tip. This fixed my problem. Up and running. Thanks. :p

---

