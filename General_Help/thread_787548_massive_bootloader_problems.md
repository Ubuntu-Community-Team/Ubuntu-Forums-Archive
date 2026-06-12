---
title: "massive bootloader problems"
date: 2008-05-09
forum: General Help
---

### Post by PappaSmurf2143 on 2008-05-09
hey guys,
i am having some problems with a bit of the boot loading. i have a raid 1 partition that has my windows on it. and a 40 gig drive that i wanted to put ubuntu 8.04 on. so i put the live cd in, and went ahead with the install. i left it all on the default options. so i start my computer up, and lo an behold, it doesn't boot. like nothing boots. so i try and go back and do the install and select the 40 gig hard drive as where the boot loader is to be installed. i try again, and once again nothing boots. i am kinda at a loss as to what to do.

the output for "sudo fdisk -l" is as follows

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x54005109

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?      119614      186453   536888706   8b  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   ?       98169      166618   549815738   75  PC/IX
Partition 2 does not end on cylinder boundary.
/dev/sda3          147270      156738    76052928+  64  Novell Netware 286
Partition 3 does not end on cylinder boundary.
/dev/sda4   *       10458       27243   134824583+  14  Hidden FAT16 <32M
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb24eb24e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       77825   625129281    7  HPFS/NTFS

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x949b949b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       14592   117210208+   7  HPFS/NTFS

Disk /dev/sdd: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xef90807b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        4660    37431418+  83  Linux
/dev/sdd2            4661        4865     1646662+   5  Extended
/dev/sdd5            4661        4865     1646631   82  Linux swap / Solaris


and the menu.lst file for my grub boot loader has this in it


title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=424d3c4a-efa2-446d-861c-af22d061358f ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=424d3c4a-efa2-446d-861c-af22d061358f ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd3,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

i want to be able to boot into xp, and into my ubuntu os as well, but without destroying the xp partition, any help would be very appriciated.

---

### Post by amohanty on 2008-05-09
Are you trying to use a RAID-1 plus a non-RAID HDD on the same system??

---

### Post by PappaSmurf2143 on 2008-05-10
the two 320gig hard drives are in a raid-1 partition. this has windows xp on it, and they are both sata drives. they are connected to my motherboards (asus P5n32-E SLI Plus) raid contoroler. the 40 gig ide hard drive is the one that i wish to put ubuntu 8.04 on, which is not raid. and i am trying to get it so i can dual boot both of them via grub.

---

### Post by jcoddington on 2008-05-10
I tried a similar install last night.  I have two SATA drives in raid 0 that have XP installed.  I added a third SATA drive to install Ubuntu 8.04 on because I don't really want to mess with my current raid configuration and XP.  I booted to the live CD installed the OS to the third drive and after rebooting it went right into XP.  It looks like GRUB didn't touch my boot sector like I thought it would.

---

### Post by amohanty on 2008-05-10
As far as I know, you will not be able to use the secondary hdd unless you mount it via LVM or something. The RAID controller gets first dibs during boot up unless you change the boot order in your BIOS in which case, you will run into the problem of not being able to dual boot WinXP at the same time as Ubuntu without changing your BIOS. 

Apparently someone found sort of a solution using LILO [http://www.linuxquestions.org/questions/linux-newbie-8/no-dual-boot-screen-with-xp-installed-first-and-linspire-375910/#post1918605](http://www.linuxquestions.org/questions/linux-newbie-8/no-dual-boot-screen-with-xp-installed-first-and-linspire-375910/#post1918605) however I would strongly recommend not going that route. Not that LILO is bad, it simply a bit more complicated than grub is. The most straight-forward solution is backup your windows settings and data and use something like partition magic to resize your windows partition, and then install Ubu in the free space.

HTH
AM

---

### Post by jcoddington on 2008-05-11
Amohanty is correct.  I was messing around with it last night and changed my hard drive boot order in the bios.   That allowed me to boot right into Ubuntu.

---

