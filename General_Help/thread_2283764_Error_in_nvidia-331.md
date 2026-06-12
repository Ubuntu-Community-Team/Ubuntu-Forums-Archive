---
title: "Error in nvidia-331"
date: 2015-06-24
forum: General Help
---

### Post by maxyman3400 on 2015-06-24
I have Ubuntu 14.10 and my drivers refuse to work. I can not change them due to some kind of deep error in nvidia-331. This is probably the result of the a prior fix which involved completely reconstructing my computer. I have no idea what is happening and the last time this happened my entire computer refused to even get to the start menu. I would provide you with an error report but now the error report does not send and it doesn't even try to change drivers.

EDIT: Now I can not download/install any software because of a failure in nvidia-331.

```

Removing nvidia-331 (331.113-0ubuntu1~xedgers14.04.1) ...
stop: Unknown instance: 
userdel: user nvidia-persistenced is currently used by process 1486
dpkg: error processing package nvidia-331 (--remove):
 subprocess installed post-removal script returned error exit status 8
Removing libatk-wrapper-java-jni:amd64 (0.30.4-4) ...
Removing libatk-wrapper-java (0.30.4-4) ...
Removing openjdk-7-jre:amd64 (7u79-2.5.5-0ubuntu0.14.10.2) ...
Processing triggers for libc-bin (2.19-10ubuntu2.3) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for bamfdaemon (0.5.1+14.10.20140925-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.22-1ubuntu2) ...
Processing triggers for mime-support (3.55ubuntu1.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Errors were encountered while processing:
 nvidia-331
Error in function: 

```

---

### Post by dino99 on 2015-06-24
if you think that issue is related to nvidia-331 driver; then purge it then reinstall it

> sudo apt-get purge nvidia*
sudo apt-get install nvidia-331

indeed use the ubuntu archive package, and avoid untrusted source like ppa

---

### Post by maxyman3400 on 2015-06-24
I have tried this around 8 times before this and I get this every time ```
 Removing nvidia-331 (331.113-0ubuntu1~xedgers14.04.1) ...stop: Unknown instance: 
userdel: user nvidia-persistenced is currently used by process 1486
dpkg: error processing package nvidia-331 (--remove):
 subprocess installed post-removal script returned error exit status 8
Errors were encountered while processing:
 nvidia-331
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

What should I do from here

---

### Post by maxyman3400 on 2015-06-24
Now I can not upgrade from 14.10 to 15.04 for there is an error.

---

### Post by efflandt on 2015-06-24
You are supposed to use **ppa-purge** to remove or comment out specific ppa's from the source list and remove any ppa packages before doing any Ubuntu version upgrades. I am using xorg-edgers for a newer nvidia version (currently nvidia-352). But why would you even use a ppa for nvidia-331 when both nvidia-331 and nvidia-331-updates packages were in the normal 14.04 reposititories?

If you upgraded 14.04 to 14.10 without purging the ppa and ppa packages, that may have tripped something up (different Ubuntu 14.04 nvidia package version running in 14.10?). When I have upgraded nvidia driver versions, nvidia-persistenced was automatically killed (but I forget if that was using synaptic and/or routine updates from Update Manager). I have installed/purged a number of nvidia versions from 14.04 because nvidia-current (or nouveau) would not work with new Maxwell chip, nvidia-331 or nvidia-331-updates worked, but I have used various newer versions from the ppa to play around with video overclocking (which requires 337 or newer).

---

### Post by grahammechanical on 2015-06-24
You can at the Grub boot menu select Advanced options for Ubuntu and then select Recovery Mode and the Resume. That will load Ubuntu using a fall back open source video driver called llvmpipe. That may get you to a working desktop where you can use Additional Drivers to change to Nouveau. If that succeeds shutdown and restart a couple of times to get Ubuntu working from a good profile and then try Additional drivers again.

My advice would be not to upgrade in expectation of fixing a problem. That does not usually work. Soon you will need to upgrade to 15.04 as 14.10 is near to reaching end of life. Before upgrading revert to using Nouveau. That is my advice.

Regards

---

