---
title: "Dual boot with NTLDR: more than one instance of GRUB?"
date: 2007-08-20
forum: General Help
---

### Post by guitonoklops9 on 2007-08-20
I'd like to use the NTLDR to dual boot between Windows XP and Ubuntu FF but am apparently getting lost somewhere (still new to Linux).   I've checked out a lot of other peoples problems with this and their threads, but have not yet found a solution to mine.

Inside my computer, there are 4 physical drives: 2 80GB SATA drives set up in a RAID 1 configuration which hold the XP installation (NTFS), 1 250GB drive holding music files (NTFS), and 1 80GB drive split into three partitions for Ubuntu (root, swap, ext).

I can successfully boot to XP (which boots by default).  If I enter the BIOS, I can change the boot hard drive and successfully boot Ubuntu.  I've been trying to configure the NTLDR to chain boot GRUB but am unsuccessful.  I think actually there may be two separate copies of GRUB installed, one on the Ubuntu drive (this one works) and maybe one on the music drive (doesn't work?) but am not sure how to find out if this is true.

below are some of the things I have tried:

I copied the Ubuntu .mbr using:

dd if=/dev/hdc of=~/Desktop/Ubuntu.mbr bs=512 count=1

Then copied this file to a USB drive, booted XP, and copied the "Ubuntu.mbr" to the C:\ dir.  I altered the "boot.ini" file by adding a line at the end:

C:\Ubunutu.mbr Ubuntu 7.04 Linux Fiesty Fawn

If I restart the machine I now get a choice of OS's upon start up between XP or Ubuntu.  After I select the Ubuntu entry,  I see the word "GRUB" in the top left hand of my screen but GRUB does not start and the system does nothing.  In Ubuntu this is what I get from fdisk:
==========================================
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/hdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   ?       13578      119522   850995205    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hdb2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/hdb3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/hdb4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        9327    74919096   83  Linux
/dev/hdc2            9328        9729     3229065    5  Extended
/dev/hdc5            9328        9729     3229033+  82  Linux swap / Solaris
==========================================
sda1 and sdb1 are clearly my 2 XP hard drives (RAID 1).  hdc1, hdc2 and hdc5 appear to be my Ubuntu drive and partitions.  However, I am not really sure whats going on with hdb1-4.  That is probably the music drive but I did not partition that drive originally.  I think during the Ubuntu install it may have done something to the drive and maybe there is a duplicate (non-working) version of GRUB.

Also tried to reinstall GRUB with: "grub-install hdc0"...no luck.
Also tried a program bootpart to point NTLDR to GRUB...no luck.

I am now at the upper limit of my understanding, could someone please point me in the right direction.  Thanks!

Luke
:guitar:

---

### Post by logos34 on 2007-08-20
Windows ntldr can't boot linux--you need to use **grldr**.

Either use **WinGrub** 

[http://sourceforge.net/projects/grub4dosr](http://sourceforge.net/projects/grub4dosr) 
[http://users.bigpond.net.au/hermanzone/p9.html](http://users.bigpond.net.au/hermanzone/p9.html)

Or get the Grub4dos zip from sourceforge, extract grldr file to windows C: directory, and add this line to boot.ini:

**c:\grldr="Ubuntu"**

Create a new folder and subfolder in C: called **boot\grub** and copy /boot/grub/menu.lst to it. ([fs-driver]("http://www.fs-driver.org/download.html") will enable windows read+write support to ext3 linux).  Don't forget to edit the 'root' lines in menu.lst--linux drive/root will become (hd1,0) or (hd2,0)


Are you sure you can't boot you windows RAID array from grub on hdc? Because that would be the best way.

---

### Post by logos34 on 2007-08-20
Not sure what's up with hdb.  You might try checking the bios to see if it's detecting the drive correctly ('auto' is usually the best setting)

Can you mount your windows raid array in linux?  And/or how does it show up in Gparted?

**sudo gparted**

---

