---
title: "No longer booting to grub and Ubuntu Partition not longer showing up"
date: 2013-11-10
forum: General Help
---

### Post by nexusvergil on 2013-11-10
Hey everyone,

So somehow I was unable to boot into grub (if got the "error: no such partition grub rescue" message).  So I ran boot-repair from a USB and now I just boot straight into Windows rather than going to the grub screen to select the operating system.  Additionally, the other partition doe snot appear when I look for it in Windows.  I tried running boot repair again (this time from a 13.04 USB rather than the 12.04 USB i used for the first attempt).  Any help would be much appreciated.  Thanks! (here is the pastebin from the second boot-repair: [http://pastebin.ubuntu.com/6392050/](http://pastebin.ubuntu.com/6392050/))

Running: 13.04 and Windows 7

---

### Post by deadflowr on 2013-11-10
Since your pastebin boot repair output doesn't list any linux partitions, I'm going to guess that this is a wubi set up?

This might help
[https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu)

Or you installed Ubuntu on a Windows file system type partition and since that might cause problems, the piper has finally come.
Hopefully it's a wubi install though.
Just a guess.

---

### Post by nexusvergil on 2013-11-10
Thanks for the response!  However, I cannot run chkdsk on the drive where Ubuntu is installed because that drive no longer appears in windows.  I have a 256GB SSD and windows shows 150GB allocated to windows 7 (with 15GB allocated to recovery) and the other 100GB not allocated anywhere (ie I think the partition is still there somehwere, but I cant access it).

---

### Post by Impavidus on 2013-11-10
In the first part of the extended partition there is about 75GB unallocated. If that is where your ext4 partition used to be, it's gone. I hope you have backups, else you need data recovery: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery). As the disk space is now unallocated, not used for something else, chances are you may recover quite a bit.

Other have posted more valuable post on this subject all over the forum.

Have you any idea what could have caused this problem?

---

### Post by deadflowr on 2013-11-10
chkdsk is a windows program.
It fixes problems on the windows partition.

But as states before, you don't have a partition listed for linux.

NTFS are Windows file system types and aren't linux file system types.

Linux file system types include EXT 2,3,4, BTRFS, REISERFS, and probably several others.
Normal linux file system type is EXT 4, though 2, or 3 are normal as well.

But for naught, because your partition layout has none of those, only vfat, fat32, and ntfs.

Edit: Ninja'd by a better answer.

---

### Post by bcbc on 2013-11-10
I'd try running testdisk and see whether it can recover the /dev/sda4 partition that's missing. I would guess it can. If it doesn't testdisk comes with photorec which can recover the missing data (as mentioned in that link).

To install testdisk:
```
sudo apt-get install testdisk
```

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by nexusvergil on 2013-11-10
Thanks everyone.  I ran testdisk from a 13.04 usb and it reports that I have my 70 GB Linux partition and another partition called "Linux swap".  I'm going through the testdisk docs now to figure out how to recover.

---

### Post by nexusvergil on 2013-11-10
This is what Teskdisk gave me for partition structure:


Disk /dev/sda - 256 GB / 238 GiB - CHS 31130 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0  32 33    25 126 37     407552 [SYSTEM]
 2 P HPFS - NTFS             25 126 38 19910  94 15  319450487
 3 E extended LBA         19910 104 33 31130 201 31  180255410
 5 L HPFS - NTFS          29031  94 56 31117  27 14   33507328 [RECOVERY]
   X extended             31117  27 15 31130 201 31     219824
 6 L FAT32                31117  28 16 31130 201 31     219760 [HP_TOOLS]


This is what testdisk gave afte "quick search":
Disk /dev/sda - 256 GB / 238 GiB - CHS 31130 255 63
     Partition               Start        End    Size in sectors
>  HPFS - NTFS              0  32 33    25 126 37     407552 [SYSTEM]
   HPFS - NTFS             25 126 38 19910 104 34  319451136
   Linux                19910 104 35 28534 243 61  138553344
   Linux Swap           28535  21 31 29030 252 22    7966720
   HPFS - NTFS          29031  94 56 31117  27 14   33507328 [RECOVERY]
   FAT32 LBA            31117  27 15 31130 223  5     221184 [NO NAME]

I am not sure if I should changed any of these partitions to "primary bootable", "primary", "logical", "extended", "deleted".  Any advice on regarding this categorization would be appreciated.

This is what testdisk's deep search returned:
The harddisk (256 GB / 238 GiB) seems too small! (< 269 GB / 250 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partitions can't be recovered:
     Partition               Start        End    Size in sectors
>  Linux                24104 243 12 32729 127 38  138553344
   Linux                24105  85 45 32729 225  8  138553344
   Linux                24106  90 49 32730 230 12  138553344
   Linux                24106 155 50 32731  40 13  138553344
   Linux                24111 116  6 32736   0 32  138553344




I am not quite sure what I should do in terms of next steps, so any advice would be great.  Thanks!

---

### Post by bcbc on 2013-11-10
The missing partitions are Logical partitions.

---

