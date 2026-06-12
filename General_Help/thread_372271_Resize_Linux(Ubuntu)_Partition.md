---
title: "Resize Linux(Ubuntu) Partition"
date: 2007-02-28
forum: General Help
---

### Post by !nvincible on 2007-02-28
**Hi All,**

I am running short of space in my Ubuntu Partition I just want to resize my partition to provide extra space
When issue parted command it gives me following structure of Harddrive

[COLOR="Blue"]Disk geometry for /dev/hda: 0kB - 40GB
Disk label type: msdos
Number Start End Size Type File system Flags
1 32kB 5240MB 5239MB primary ntfs boot
2 5240MB 40GB 35GB extended lba
5 5240MB 10GB 5239MB logical fat32
6 10GB 16GB 5239MB logical fat32
7 16GB 17GB 1053MB logical linux-swap
8 17GB 27GB 10GB logical fat32
9 27GB 39GB 12GB logical ext3
10 39GB 40GB 1020MB logical ext3[/COLOR]

In this case I want to merge my 9 and 8 partition since I have nothing important in partition no 8 I can even format it...so no issue regarding that, but the problem is I am having linux partition in partition no 9 and when I issue resize 9 17GB 39GB command it gives me an error ...

This is I get when I do fdisk -l

[COLOR="Blue"]Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 637 5116671 7 HPFS/NTFS
/dev/hda2 638 4865 33961410 f W95 Ext'd (LBA)
/dev/hda5 638 1274 5116671 b W95 FAT32
/dev/hda6 1275 1911 5116671 b W95 FAT32
/dev/hda7 1912 2039 1028128+ 82 Linux swap / Solaris
/dev/hda8 2040 3314 10241406 83 Linux
/dev/hda9 3315 4741 11462346 83 Linux
/dev/hda10 4742 4865 995998+ 83 Linux[/COLOR]

[B]
How can I solve this problem[/B]
Thankx in advance...

---

### Post by CameronCalver on 2007-02-28
are you doin this using the live cd?

---

### Post by Cobikegeek on 2007-02-28
So is hda9 your ubuntu root partition?  I think you can only resize from the end sectors of a partition, so you could only increase hda9 by shrinking hda10.  You could increase hda8 using the space in hda9, but that would probably require a reinstall of ubuntu into the resized hda8 or making more settings changes than I can advise you about.

Edit:  Sorry Invincible.  I checked my knoppix hacks book and realized that you can resize a partition at either the beginning or the end, the space just has to be continuous (ie. coming from either the previous or next partition)  Make sure the sectors match with the beginning or end of the partition you are resizing because the partition numbers don't necessarily indicate whether a partition is adjacent.  For example, on my system, the windows restore partition is sda2, but it is physically at the end of the drive and not adjacent to sda1.  

Your hda8 and hda9 do appear continuous according to the partition info you provided, so you should be ok.  I'm not looking at gparted, but the basic steps are to boot from the live cd (so no partitions are mounted), start gparted, select your hard drive from the device list, select hda8 and choose to delete hda8.    Then select hda9 and resize at the beginning of the partition to grab the space from hda8.  It's always a good idea to backup before editing partitions because data loss can occur.  Any data on hda8 will definitely be gone.

---

