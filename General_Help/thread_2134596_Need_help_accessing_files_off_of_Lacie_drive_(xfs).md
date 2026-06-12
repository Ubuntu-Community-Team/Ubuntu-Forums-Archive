---
title: "Need help accessing files off of Lacie drive (xfs?)"
date: 2013-04-11
forum: General Help
---

### Post by jtadeo51 on 2013-04-11
Hi guys,

I'm currenting running Ubuntu 12.10 off of a flash drive (just running it off of ram). I have a Lacie drive connected via USB, but it's not showing up as an available disk so I can't browse the contents of it. 

Could someone please help me mount this thing so I can recover some files.
here are the fdisk -l results

this@this:/media$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcca3b8b5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   624502783   312250368    7  HPFS/NTFS/exFAT
/dev/sda2   *   624502784   625117183      307200    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 7862 MB, 7862353920 bytes
37 heads, 37 sectors/track, 11217 cylinders, total 15356160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8064    15356159     7674048    c  W95 FAT32 (LBA)

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x346890e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63     2008124     1004031    5  Extended
/dev/sdc2         2008125   976768064   487379970   83  Linux
/dev/sdc5             126      257039      128457   82  Linux swap / Solaris
/dev/sdc6          257103      273104        8001   83  Linux
/dev/sdc7          273168      289169        8001   83  Linux
/dev/sdc8          289233      546209      128488+  83  Linux
/dev/sdc9          546273     2008124      730926   83  Linux
this@this:/media$ 

Thanks!

---

### Post by conradin on 2013-04-11
Im not sure where youre getting xfs filesystem do you mean to say explicitly, you know it is xfs?
[http://www.win.tue.nl/~aeb/partitions/partition_types-1.html](http://www.win.tue.nl/~aeb/partitions/partition_types-1.html)

which device is it?
/dev/sda or /dev/sdc?

if you actualy have an xfs partition, then you can try installing xfsprogs,
which may give you some support. 
In my expirience, the best xfs support was in warty warthog Ubuntu v4.10?
Thats a distro that was out when xfs was popular. For whatever reasons, its always seemed to work better than more modern support. 

.. oh hey is that an XFat partition youre trying to mount? You might have to download support for XFAT. 
which partitions are you having trouble mounting?

---

### Post by jtadeo51 on 2013-04-11
> **conradin said:**
> Im not sure where youre getting xfs filesystem do you mean to say explicitly, you know it is xfs?
[http://www.win.tue.nl/~aeb/partitions/partition_types-1.html](http://www.win.tue.nl/~aeb/partitions/partition_types-1.html)

which device is it?
/dev/sda or /dev/sdc?

if you actualy have an xfs partition, then you can try installing xfsprogs,
which may give you some support. 
In my expirience, the best xfs support was in warty warthog Ubuntu v4.10?
Thats a distro that was out when xfs was popular. For whatever reasons, its always seemed to work better than more modern support. 

.. oh hey is that an XFat partition youre trying to mount? You might have to download support for XFAT. 
which partitions are you having trouble mounting?

Thanks for the reply.

I guess I'm not too sure if the Lacie drive is running an XFS partition or not. I just did a quick google search and many people claim that it is an xfs partition. Windows doesn't recognize it nor does OSX

---

### Post by conradin on 2013-04-16
Any OSX or MS Windows OSes probably wont recognize the numerous linux partition types. I think 83 is the flag for ext2 or ext3.
try a warty warthog boot disk and see if it comes up.

---

### Post by CdPFwsx on 2013-10-18
I had a Lacie Edmini 500GB ethernet disk that, one day, ceased to work. I then later needed to recover few files that were on that HD. Connecting it to my Windows Laptop, I find out that there were 5 Linux partitions on it: 2 RAW and 3 Etx2. Using Ext2FSD Volume Manager, I managed to mount the Ext2 partitions, but I found on there just some Edmini system environment files/folders. The actual data were on the bigger partition (~460GB) and it was a RAW one. So, you can mount it but not access it (Windows keep asking if you wanna format it).
If you are in this situation, don't waste time to find a way to mount it on Windows (neither with virtual - or kinda of virtual - Linux environment, like coLinux).
[COLOR=#0000ff]SOLUTION HERE >> [/COLOR]_**Just download an UBUNTU ISO**_ (I took the 9.04 [here]("http://www.4shared.com/file/jdbH_xOV/ubuntu-904-desktop-i386.html")), burn it and run it as LIVE CD ("Try Ubuntu without any change to your computer"), and connect the Hard Disk removed from the LaCie Edmini, using kinda docking station/SATA-USB adapter... You'll have your partitions mounted on your desktop at startup. You can now open all the partitions and get your files back. In case you can't access to some folders, cause you don't have permissions, just access it using the command: 
[COLOR=#0000cd][FONT=courier new]sudo nautilus[/FONT][/COLOR]
That's it.

Hope this could help anyone passing here while seeking information about how to mount XFS partition on Windows... or just how to mount them. So that you would not have to waste time, like I did.
Cya!

---

