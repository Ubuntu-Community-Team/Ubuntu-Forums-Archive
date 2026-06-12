---
title: "Ubuntu MBR"
date: 2007-12-06
forum: General Help
---

### Post by ploik on 2007-12-06
i have 2 hard drives, one has ubuntu, and the other has XP, after switching hard drives, neither worked, so i switched them back, and now it doesnt dual boot anymore. i installed ubuntu again on some of the extra space i have on the ubuntu hard drive, and now it dual boots again, is there a way to copy the MBR from the newly created partition onto the older one and replace it so i can dual boot without wasting the extra 2GB for the unneeded extra ubuntu? or at least where the MBR for ubuntu is? i use ubuntu 7.10 gutsy, if that helps.

---

### Post by uidb4056 on 2007-12-06
I suggest you to read carefully [http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

There is a lot of explanations about multiple boot the GRUB and MBR

---

### Post by ploik on 2007-12-06
i read that already, and ubuntu is already installed, and i dont wanna re-install it, it says the only other optiono is to use super grub disk (i used it and it only boots the HD), the last option is to use the live cd to re-install the grub loader, but i dont know how, all i see in the live cd is "start/install, start/install recovery, check cd for errors, and boot HD" can you tell me where to go on the live cd to re-install the drub loader?

---

### Post by meierfra on 2007-12-06
To be able to give you detailed instruction I need some information. Open a terminal (Applications->Accessories->Terminal) . Type
```
sudo fdisk -l
```

and 

```
cat /boot/grub/menu.lst
```

(both "l" are lowercase L)

Copy the output and post it here.


(Do this in ubuntu. You don't need the LIveCD)

---

### Post by g2g591 on 2007-12-06
OK, for one thing the ubuntu installer installs grub to the mbr of the whole harddrive, not just that one partation. Do like the above guy said and we can help much much more.

---

### Post by hogwartsnigel on 2007-12-06
sorry guys but couldn't the guy benefit from downloading the Super Grub Disc, it'll assit in recovery and repair of bad boot

Nigel

---

### Post by meierfra on 2007-12-06
deleted

---

### Post by bodhi.zazen on 2007-12-06
> **ploik said:**
> i have 2 hard drives, one has ubuntu, and the other has XP, after switching hard drives, neither worked, so i switched them back, and now it doesnt dual boot anymore. i installed ubuntu again on some of the extra space i have on the ubuntu hard drive, and now it dual boots again, is there a way to copy the MBR from the newly created partition onto the older one and replace it so i can dual boot without wasting the extra 2GB for the unneeded extra ubuntu? or at least where the MBR for ubuntu is? i use ubuntu 7.10 gutsy, if that helps.

Grub is a little hard to understand at first.

Here is a nice tutorial on how to restore grub :

[uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki]

In a nut shell :

The MBR is NOT on a partition, but is on the very start of your first hard drive.

When you change the physical configuration of your system you will need to update grub, installing it into your MBR.

Grub goes through "stages", but eventually looks for /boot/grub/menu.lst , which is the main configuration file for grub.

To configure grub, you need to understand linux partitioning terminology :

[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

==========

OK , so your first hard drive is say sda and your second is sdb

Say Ubuntu is on sda1 and windows on on sdb1

Boot the ubuntu CD and follow the advice on how to re-install grub.

The problem you then have is you need to update /boot/grub/menu.lst to reflect the new hardware configuration.

You can do this manually. The grub sanzas look like this :

windows
root (hdx,y)  # Update this line to the new location of windows in grub partitioning terminology
chainloader +1

Ubuntu
root (hdx,y) # Update this line to the new location of windows in grub partitioning terminology
kernel /boot/vmlinux-xyz root=/dev/xxx ro quiet splash
# update the kernel line so root=/dev/xxx is the Ubuntu partition in linux partitioing terminology
initrd /boot/initrd-xyz

You also need to update the grub configuration in /boot/grub/menu.lst

See this post for how to do that : 

[http://ubuntuforums.org/showthread.php?t=316237](http://ubuntuforums.org/showthread.php?t=316237)

---

