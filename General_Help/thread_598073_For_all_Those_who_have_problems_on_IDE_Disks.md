---
title: "For all Those who have problems on IDE Disks"
date: 2007-10-31
forum: General Help
---

### Post by harishgayatri on 2007-10-31
If your IDE Hard Disk is shown as SCSI (sda,sdb,)etc. Use the following Method for DMA
on your IDE Channels.As well as Edit your **fstab** File.

************
edit /etc/initramfs-tools/modules, and adding this lines:

#piix
ide_generic
ide_cd
ide_disk

# blacklist bad driver
blacklist ata_piix

# prevent unnecessary modules from being loaded (you don't need to do this)
blacklist ata_generic
blacklist libata
blacklist scsi_mod

after editing:

sudo update-initramfs -u

********************************************************************************
Edit /etc/fstab and change sda,sdb,sdc to hda,hdb,hdc

**AND DO NOT FIDDLE with anything ELSE**
********************************************************************************

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda5
UUID=a1d3658a-366b-45c1-ac02-675bd1c25c97 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=6A64235064231E77 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
/dev/hda3 
UUID=0E34812F34811B3B /media/hda3     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda6
UUID=a494db3a-d6a1-4f48-b263-61d6314ec410 none            swap    sw              0       0
/dev/hdc      /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd      /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

****************************************************************************
Edit the Folder /media/sda,sdb,sdc to /media/hda,hdb,hdc by using **gksu nautilus** commmand in the run window.

I tried this soultion on My Gutsy 7.10 Installation and it works perfectly after a reboot.

**The credit goes to "Fabio Povoledo" in this forum for posting this solution**

Enjoy.:lolflag::lolflag::lolflag:
**harishgayatri**

---

### Post by frodon on 2007-10-31
Just in case you don't know, if your ide drive appear as SCSI this is not a problem, it is because ide drives are handled by sata drivers (which have DMA enabled by default) now.
So except if you have hard drive slowdown issues do not use these instructions.

**And please stop advising users to use device path in fstab instead of UUID, these kind of advices are responsible of many unbootable kernels after upgrade to new ubuntu release or at least explain users that when they will upgrade their ubuntu box to the next version they will have to know how to boot another kernel or use a live CD to fix their fstab**

---

### Post by ofb on 2007-11-03
> **frodon said:**
> So except if you have hard drive slowdown issues do not use these instructions.

I've just used this to re-enable my CDRW which 7.10 could not detect.
[http://ubuntuforums.org/showthread.php?p=3689571#post3689571](http://ubuntuforums.org/showthread.php?p=3689571#post3689571)

I'd love to know what it's all about. After a few hours of reading bug reports I'm no closer to understanding.

> And please stop advising users to use device path in fstab instead of UUID, these kind of advices are responsible of many unbootable kernels after upgrade to new ubuntu release or at least explain users that when they will upgrade their ubuntu box to the next version they will have to know how to boot another kernel or use a live CD to fix their fstab

Please explain, or provide a link that does.

---

### Post by cb474 on 2007-11-04
What if I have SATA drives? Could these instructions still be helpful?

I'm having a problem with slow reading of FAT32 partitions only, described here (Ext3 partitions on the same drives are fine, not slow):

[http://ubuntuforums.org/showthread.php?t=603042](http://ubuntuforums.org/showthread.php?t=603042)

---

### Post by wolframarnold on 2007-11-15
The instructions worked to boot out the sata drivers. However, I seem to **have lost DMA!!!**
```

$> sudo hdparm -d /dev/hda
/dev/hda:
 using_dma     =  0 (off)

```
Trying to set DMA (either via sudo hdparm -d1 or /etc/hdparm.conf) **fails!**

I read elsewhere that including the chip-set specific ide module would fix this, but Gutsy no longer includes the "piix" module.  Major bummer!  I'm at a loss, because the sata drivers give me freezes and exceptions like crazy, as documented in many places here.  I'm seriously considering going back to Feisty.

---

### Post by frodon on 2007-11-16
Once again DMA is activated by default on all SATA disks and hdparm is made for IDE drives therefore hdparm commands have no effect on SATA drives.

---

### Post by wolframarnold on 2007-11-16
> **frodon said:**
> Once again DMA is activated by default on all SATA disks and hdparm is made for IDE drives therefore hdparm commands have no effect on SATA drives.

Yeah, I know this, but the SATA drivers suffer from the drive freezing problem that I've yet to see a good solution to, short of recompiling some experimental kernel with patches.  Why did the standard chipset drivers get removed from Gutsy??? Next I'm trying to compile the piix as a module, to get DMA back, using the standard ide drivers.

---

### Post by Kablooie!! on 2008-01-15
Hi all,

Would this DMA problem prevent you from actually mounting the drives, like I posted here:

[http://ubuntuforums.org/showthread.php?p=4140064#post4140064](http://ubuntuforums.org/showthread.php?p=4140064#post4140064)

??

Thanks,
Grant

---

