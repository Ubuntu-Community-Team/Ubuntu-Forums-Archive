---
title: "[SOLVED] Big problems with grub and MBR!!!!"
date: 2008-01-07
forum: General Help
---

### Post by doctorgreg on 2008-01-07
Ok I installed vista first.  Then I installed Ubuntu.  Then I shrunk the ubuntu partition to allow me to install XP.  After I installed XP I had no grub menu.  My comp would automatically boot into XP.  I got the grub menu back.  But i try to boot ubuntu and I get Error 17  cannot mount partition.  Also in my grub menu under other OS I have Windows Vista. I click on the Vista in the grub and it loads into XP.  Xp don't even show up in the grub menu.  So basically i lost my vista and ubuntu.  Don't know where to go from here?  Thanks.

---

### Post by tech9 on 2008-01-07
> **doctorgreg said:**
> Ok I installed vista first.  Then I installed Ubuntu.  Then I shrunk the ubuntu partition to allow me to install XP.  After I installed XP I had no grub menu.  My comp would automatically boot into XP.  I got the grub menu back.  But i try to boot ubuntu and I get Error 17  cannot mount partition.  Also in my grub menu under other OS I have Windows Vista. I click on the Vista in the grub and it loads into XP.  Xp don't even show up in the grub menu.  So basically i lost my vista and ubuntu.  Don't know where to go from here?  Thanks.

you can always boot up with supergrub disk.. you can even repair your grub loader

download supergrub disk

[http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)

burn it as an ISO to a CD

Boot up into supergrub and repair from there.

hope this helps - Good Luck :)

---

### Post by doctorgreg on 2008-01-07
I already have supergrub disk and i went in there but did not know what to chose.  There are so many options in there and i don't want to make things worse by doing the wrong thing

---

### Post by doctorgreg on 2008-01-07
this is what i get with sudo fdisk -l

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7462    59935648+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hda2            7463        7593     1052257+  82  Linux swap / Solaris
/dev/hda3            7594        9548    15703537+   f  W95 Ext'd (LBA)
/dev/hda4            9549       12161    20988922+  83  Linux
/dev/hda5            7594        9548    15703506    7  HPFS/NTFS
ubuntu@ubuntu:~$ 

note there seems to be a problem with my partition 1 which is vista!

---

### Post by doctorgreg on 2008-01-07
UPDATE:  I got ubuntu loading up fine but when I chose vista loader in grub it doesnt give me and option to pick between vista or xp.  It just loads right into xp.  I'm lost now.  Please help.

---

### Post by Dr. C on 2008-01-07
This thread describes a  triple boot between Ubuntu, XP and Vista. 
[http://ubuntuforums.org/showthread.php?t=220452]("http://ubuntuforums.org/showthread.php?t=220452")
The simplest way to do this is to first install XP, then Vista and finally Ubuntu. Basically Vista is aware of XP and Ubuntu is aware of both. When performing a repair I would restore XP first,  then the Vista bootloader (to get a dual boot XP / Vista), and finally restore GRUB to get a triple boot.

Here are some more resources
[http://apcmag.com/dualboot]("http://apcmag.com/dualboot")

---

### Post by doctorgreg on 2008-01-08
Well i didn't really want to have to wipe everything out.  So basically there is no way of me being able to boot into my vista anymore?

---

### Post by doctorgreg on 2008-01-08
I have figured it out by myself and with a little googling.  I installed easyBCD in XP and rewrote the vista mbr and saved it.  Then rebooted.  It automatically boots vista.  Then while in vista I use the same easyBCD.  Once in BCD click on Add/Remove Entries.  Just selected XP in the list, chose which drive it is and saved it.  Then put ubuntu live cd in disc tray.  Reboot into the disk.  Then i just went in the terminal and did sudo grub, root (hd0,3), setup (hd0).  Then it will say succeeded.  Just rebooted and voila.  I have grub and my vista and xp in the mbr.  Thanks for your suggestions and help.

---

