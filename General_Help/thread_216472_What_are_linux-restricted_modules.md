---
title: "What are linux-restricted modules?"
date: 2006-07-15
forum: General Help
---

### Post by Boomy on 2006-07-15
I was doing some upgrades and got an error about a linux-restricted module dependency. I'm afraid to restart my machine now, can I remove these?

---

### Post by matthias_k on 2006-07-15
I think the package description says it all:
> This package provides restricted modules for Linux version 2.6.15 on
Pentium Pro/Celeron/Pentium II/Pentium III/Pentium IV.
Currently the following modules are included:
 - madwifi (Atheros)
 - fglrx (ATI)
 - nvidia
 - fcdsl, fcdsl2, fcdslsl, fcdslslusb, fcdslusb, fcdslusb2, fcdslusba,
   fcpci, fcpcmcia, fcpcmcia_cs, fcusb, fxusb (AVM ISDN)

These modules are "restricted" because they are not available under a
completely Free licence.

If you don't use any of these modules, you can remove the package.

---

### Post by Boomy on 2006-07-15
> **matthias_k said:**
> I think the package description says it all:

If you don't use any of these modules, you can remove the package.

I'm a newbie, so I'm not sure, I do have an nvidia graphics card, but I'm using the nvidia-glx driver.

---

### Post by matthias_k on 2006-07-15
Hmm, I don't have an nVidia graphics card, so I'm not sure how the proprietary driver module is called. Do you get hardware-accelerated 3D? If so, you're most likely using the proprietary driver, in which case you need the restricted modules package.

If you're unsure, just keep the package. Fur further help you should post the complete error message here, saying "I got an error while doing XYZ" is not very insightful :)

---

### Post by Boomy on 2006-07-15
Here are the errors I get after installing anything in synaptic. 

E: linux-restricted-modules-2.6.15-26-k7: subprocess post-installation script returned error exit status 16
E: linux-restricted-modules-k7: dependency problems - leaving unconfigured
E: linux-k7: dependency problems - leaving unconfigured

---

### Post by Boomy on 2006-07-15
Ok, here are some more specific details. 

nvidia-glx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 26 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking, 0B of additional disk space will be used.
Setting up linux-restricted-modules-2.6.15-25-k7 (2.6.15.11-2) ...
Cannot create link /etc/mtab~
Perhaps there is a stale lock file?

dpkg: error processing linux-restricted-modules-2.6.15-25-k7 (--configure):
 subprocess post-installation script returned error exit status 16
dpkg: dependency problems prevent configuration of nvidia-glx:
 nvidia-glx depends on nvidia-kernel-1.0.8762; however:
  Package nvidia-kernel-1.0.8762 is not installed.
  Package linux-restricted-modules-2.6.15-26-386 which provides nvidia-kernel-1. 0.8762 is not installed.
  Package linux-restricted-modules-2.6.15-23-386 which provides nvidia-kernel-1. 0.8762 is not installed.
  Package linux-restricted-modules-2.6.15-25-k7 which provides nvidia-kernel-1.0 .8762 is not configured yet.
  Package linux-restricted-modules-2.6.15-25-386 which provides nvidia-kernel-1. 0.8762 is not installed.
  Package linux-restricted-modules-2.6.15-26-k7 which provides nvidia-kernel-1.0 .8762 is not installed.
dpkg: error processing nvidia-glx (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-restricted-modules-2.6.15-25-k7
 nvidia-glx
E: Sub-process /usr/bin/dpkg returned an error code (1)
matt@ubuntu:~$

---

### Post by Boomy on 2006-07-15
This link saved my ***. 

[http://www.ubuntuforums.org/showthread.php?t=213420](http://www.ubuntuforums.org/showthread.php?t=213420)

After rebooting, X wouldn't start, luckily I printed off some instructions that allowed me to install the kernel and now it works. :)


If it's too late and you have problems at start-up, boot in recovery mode and install the kernel metapackage via apt-get:

- Check first your architecture
Code:

uname -r

- Install the metapackage
Code:

sudo apt-get install linux-arch #replace arch with your architecture

---

