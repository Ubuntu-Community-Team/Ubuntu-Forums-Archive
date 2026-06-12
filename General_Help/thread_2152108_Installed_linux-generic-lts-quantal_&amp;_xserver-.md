---
title: "Installed linux-generic-lts-quantal &amp; xserver-xorg-lts-quantal remove 3.2.x kernels"
date: 2013-06-06
forum: General Help
---

### Post by cscj01 on 2013-06-06
I was on Ubuntu 12.04 x64 LTS.  I upgraded to the 3.5.x kernel series using the command ```
sudo apt-get install linux-generic-lts-quantal xserver-xorg-lts-quantal
```in order to be at 12.04.2 LTS.  Now I am being prompted to upgrade my 3.2.x kernel.  Why am I getting that message?  What should I uninstall so that I won't upgrade the wrong software?

BTW, my system shows I am running 3.5.0-32, but Synaptic shows nothing about the 3.5.x kernel or about the upgraded xserver stack.

Help!!!

---

### Post by Frogs Hair on 2013-06-06
The Ubuntu meta packages determine  updates for the kernel and other packages native to the release and won't recognize a manually upgraded kernel. There are threads about getting around this because users manually upgrade. If  the release came with 3.2 only improvements for 3.2 come via the update manger unless an upgrade comes from the Ubuntu end. Check threads about manually upgrading kernels.

---

### Post by cscj01 on 2013-06-06
> **Frogs Hair said:**
> The Ubuntu meta packages determine  updates for the kernel and other packages native to the release and won't recognize a manually upgraded kernel. There are threads about getting around this because users manually upgrade. If  the release came with 3.2 only improvements for 3.2 come via the update manger unless an upgrade comes from the Ubuntu end. Check threads about manually upgrading kernels.

I thought using apt-get was not a manual upgrade.  I understand that it is not an automatic update, but shouldn't Update Manager understand I have installed these 2 packages and handle my system accordingly?  If not, why does the system provide updates when I install other packages with apt-get?  I am confused here; just asking.

---

### Post by cscj01 on 2013-06-08
Okay, I believe I know what happened.  I'm just not sure why it happened.

I had three HDD's in my system; [LIST=1]
[*]my boot drive had my operating systems (dual boot Ubuntu and XP) and swap partitions
[*]one was a data only drive[*]the third was an older copy of my operating system drive.
[/LIST]
I specified in BIOS that only the CD/DVD drive and the Boot drive were to be used for booting.

  When I checked the drives after booting the system, the mount points were exactly as I had told the BIOS;[LIST=1]
[*]my boot drive was /dev/sda (and the correct HDD) and the devices and partitions were mounted at /dev/sda1-->/media/sda1 (XP), /dev/sda2-->/ (Ubuntu 12.04.2), and /dev/sda3 (swap)
[*]my data drive was /dev/sdb and was mounted at /dev/sdb1-->/media/Data
[*]my old copy HDD was /dev/sdc (also the correct HDD) and the mounts were /dev/sdc1-->/media/sdc1 (XP), /dev/sdc2-->/ (Ubuntu 12.04.2), and /dev/sdc3 (swap)[/LIST]

For some reason of which I do not know, Ubuntu was attempting to upgrade the system on sdc2.

Whenever I checked Places->Computer->File System, sda2 was displayed.  So why did Ubuntu try to use sdc2?  Is it not possible to have a copy of one's system HDD that is not the boot system HDD without Ubuntu getting confused?

In any case, after disconnecting the HDD copy, I have not gotten any updates to the 3.2.x kernel via Update Manager.

---

### Post by cscj01 on 2013-06-12
bump

---

### Post by grahammechanical on 2013-06-12
My guess is that because those Linux 3.2.0 kernels are on that Ubuntu system, then you get updates to those kernels. Use Synaptic to remove those kernels and you will not get updates to the 3.2.0 series kernels because they will not be registered as being on the system. I have several Ubuntu installs across 2 hard disks. I have never known an update (by terminal or Update Manager) to update a Ubuntu that I was not logged into. To keep several Ubuntus updated I have to load into each one and run the update.

Regards.

---

### Post by cscj01 on 2013-06-13
> **grahammechanical said:**
> My guess is that because those Linux 3.2.0 kernels are on that Ubuntu system, then you get updates to those kernels. Use Synaptic to remove those kernels and you will not get updates to the 3.2.0 series kernels because they will not be registered as being on the system. I have several Ubuntu installs across 2 hard disks. I have never known an update (by terminal or Update Manager) to update a Ubuntu that I was not logged into. To keep several Ubuntus updated I have to load into each one and run the update.

Regards.

Thanks for your comment.  I am still somewhat mystified as to how it happened, but I did remove the 3.2.x kernels and no longer get updates.  I'll mark this as solved even though I would still like to know how that can happen.

---

