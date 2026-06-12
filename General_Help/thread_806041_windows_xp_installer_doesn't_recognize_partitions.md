---
title: "windows xp installer doesn't recognize partitions"
date: 2008-05-24
forum: General Help
---

### Post by muaddib on 2008-05-24
Hi,
I am trying to re-install Windows XP Pro on my first HD, but the Windows XP installer doesn't recognize any of my partitions.
I have two internal SATA hard drives. Here is my setup:

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4290428f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8516    68404738+   c  W95 FAT32 (LBA)
/dev/sda2            8517        9495     7863817+  82  Linux swap / Solaris
/dev/sda3            9496       17100    61087162+  83  Linux
/dev/sda4           17101       30401   106840282+   5  Extended
/dev/sda5           17101       25616    68404738+  83  Linux
/dev/sda6           25617       30401    38435481   83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f800000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       12218    98141053+  83  Linux
/dev/sdb2           12219       38913   214427587+   5  Extended
/dev/sdb5           12219       16959    38082051   83  Linux
/dev/sdb6           16960       21700    38082051   83  Linux
/dev/sdb7           21701       26441    38082051   83  Linux
/dev/sdb8           26442       38913   100181308+  83  Linux
```

I know, it's kind of complicated. The important parts are:
/dev/sda1: Partition which Windows XP should be (I was going to re-format this as NTFS)
/dev/sda3: Linux root partition ('/')

The story is, I originally installed XP on /dev/sda1, then Linux with GRUB. After adding the second HD and setting up partitions, the XP install wouldn't boot. No big deal, I would just re-install XP and then re-install GRUB (I have done this before without a problem).

The problem comes up when I try to re-install Windows XP. When it asks me where I want to install windows, it does not seem to recognize my partition table at all! It lists the first HD and second HD as if there were no partitions.

Any ideas as to how I can get windows to read the partition table? My goal is to keep all of the partitions un-touched except /dev/sda1 and the boot sector.

---

### Post by logos34 on 2008-05-24
try using gparted to delete sda1 altogether.  Maybe XP installer will then see that part of the disk as empty space.

You can use TestDisk to fix the partition tables.  Be careful.  Read the [documentation]("http://www.users.bigpond.net.au/hermanzone/p21.html").

---

### Post by TeoBigusGeekus on 2008-05-24
I can't understand how you installed winxp in the first place. If you have an original copy of the os, it would never recognise sata drives as it doesn't have any drivers for it.

Solution 1:
Create your own winxp cd with nlite
[http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml]("http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml")

Solution 2:
Download your sata drivers, copy them into a floppy, press F6 during xp installation (install SCSI or RAID drivers) and let the installer find the drivers from the floppy.

Solution 3 (theoretical - illegal):
There are a lot of bloated winxp versions you could download through torrents
[http://www.torrentz.com/search?q=windows+xp]("http://www.torrentz.com/search?q=windows+xp")
that already have sata drivers in the installer, but don't do it: it's illegal...

---

### Post by muaddib on 2008-05-28
Thanks TeoBigusGeekus and logos34 for the suggestions! I did attempt to erase the partition, but XP still doesn't recognize it. I decided to just install a floppy drive (I'm sure I've got one lying around here somewhere), and load the sata drivers that way, as per TeoBigusGeekus' advice.
Thanks again!

-Muad'dib

---

