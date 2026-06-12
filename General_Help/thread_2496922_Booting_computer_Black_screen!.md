---
title: "Booting computer? Black screen!"
date: 2024-04-17
forum: General Help
---

### Post by daanheuvelbeuk on 2024-04-17
Since I have a dual boot system I have issues while booting. I am regularly watching to a black screen, no splash screen or Grub Boot Menu. I solve my problem by repeatedly pushing the reboot button on my computer when the scree stays black, until I get the boot menu. A few days ago I noticed then when I lat the "boot" process go on, e.g. stair at the black screen, Ubuntu will start up (sometimes?). Only when I see a dash ('-') appear in the top left corner of my primary display I know I will get a boot menu. And I would like to work on Windows 11 occasionally. And before I installed Ubuntu I had no boot problems with my Windows 11 system. I let the boot process run its course, still black screen, after rebooting 15 times, to be able to write this post.

I have a system with Windows on SSD (SNVS1000G), and Ubuntu on a HD. It is an ACOI x64-based PC with an AMD processor and a NVIDIA GeForce RTX 3060 graphical card. 

Anyone know what causes the "black screen at boot time"?

Edit: Added line about seeing a dash ('-').

---

### Post by yancek on 2024-04-17
If you have windows and Ubuntu on separate physical drives, it should be a simple matter of selecting the drive with windows in the one time boot option in your BIOS firmware on boot.   Select the drive with Ubuntu in the BIOS also to boot Ubuntu.  Are you trying to boot windows 11 from the Ubuntu Grub menu?  Has this option ever booted?  When you are able to boot into Ubuntu, do things appear to work normally, particularly with the graphics?  Did you install the Nvidia drivers?

If you do not resolve this, I would suggest you run boot repair and post the output here.   Go to the site at the link below and read through the page then select the 2nd option described on the page to get the software and run it with the Create Bootinfo Summary option and post the link you get here for help.  Best not to try any repairs until members here get a chance to view the information from boot repair.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by daanheuvelbeuk on 2024-04-18
The required boot-repair output to pastbin: [https://paste.ubuntu.com/p/3jcZcD9wZt/](https://paste.ubuntu.com/p/3jcZcD9wZt/)

---

### Post by daanheuvelbeuk on 2024-04-18
> **yancek said:**
> If you have windows and Ubuntu on separate  physical drives, it should be a simple matter of selecting the drive  with windows in the one time boot option in your BIOS firmware on boot.    Select the drive with Ubuntu in the BIOS also to boot Ubuntu.  Are you  trying to boot windows 11 from the Ubuntu Grub menu?  Has this option  ever booted?  When you are able to boot into Ubuntu, do things appear to  work normally, particularly with the graphics?  Did you install the  Nvidia drivers?


I actually do not know how to find out how to find out what you ask. I can answer you question about booting windows 11 from the Grub menu with yes. Things appear to work normally. And I think I have installed the Nvidia drivers:
```
~$ cat /proc/driver/nvidia/version
NVRM version: NVIDIA UNIX x86_64 Kernel Module  470.239.06  Sat Feb  3 06:03:07 UTC 2024
GCC version:  gcc version 12.3.0 (Ubuntu 12.3.0-1ubuntu1~22.04) 
```

The required boot-repair output to pastbin: [URL="https://paste.ubuntu.com/p/3jcZcD9wZt/"]https://paste.ubuntu.com/p/3jcZcD9wZt/

[/URL]Edit: I am currently 'sudo ubuntu-drivers install' and am seeing texts as 'libnvidia-cfg1-470 etc.' will be removed and 'libnvidia-cfg1-535 etc.' will be installed. If I remember correctly I had some graphical issues which I resolved by selecting the 'NVIDIA driver metapackage from nvidiea-driver-470 (proprietary)'. I will see what effect this will have.

---

### Post by oldfred on 2024-04-18
Ir installing a new/different nVidia driver you must purge before new driver installed or you get conflicts & issues.
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351)

You show 3 ESP - efi system partitions and 4 UEFI boot entries. See line 197.
But you also have an old BIOS Windows entry in sda. That should never be used, but if system default set to boot in old BIOS mode, it may try to use that entry and fail. 

Not sure what drive you have as default  or preferred. Best to have first UEFI entry as main working system and others only as alternatives.
Grub will normally boot Windows, if fast startup/hibernation off. Windows may turn it back on & then you need to directly use UEFI boot entry to turn it back off.

You can see and manage UEFI boot entries with efibootmgr.
man efibootmgr
sudo efibootmgr -v
UEFI uses GUID or partUUID for search to correct ESP. So compare UEFI entries with ESP partition's partuuid.
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid

You can change preferred UEFI boot entry with efibootmgr and -o parameter or from within your UEFI settings menu(not one time boot menu).

---

