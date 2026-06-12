---
title: "gParted: Can't have a partition outside the disk!"
date: 2012-10-21
forum: General Help
---

### Post by mph3 on 2012-10-21
I've read several other threads on similar gParted issues, but I haven't found a scenario identical to mine.

Background:  I have a Ubuntu 12.04 / Windows Vista dual boot.  My Ubuntu partition (dev/sda3) is almost full, and I need to reallocate some space from the Vista partition (dev/sda2).  I ran gParted, and it showed my entire disk as unallocated;  info stated "overlapping partitions".  Forum research led me to try testdisk.  After testdisk, I received ```
 unknown filesystem
  grub rescue>
```Additional forum research led me to run **boot-repair**, which worked.  

Now back to trying to re-size my partitions, I run gParted and the whole disk still shows as unallocated, but this time the info states "Can't have a partition outside the disk!"

See below - [COLOR="Red"]/dev/sda4[/COLOR] appears to be the problem.  sda4 I cannot mount, but all of my other partitions I can mount (except swap sda5).  When attempting to mount sda4, I get either "you must specify the filesystem type" or the mount command hangs.  I don't know whether this partition is essential or if it is an error in the partition table, since it appears to occupy same space as swap in sda5 & Windows in sda6.  I am skeptical of running testdisk again since it caused issues the first time.  How can I determine whether sda4 is needed or can be deleted? [COLOR="Blue"] Any help would be greatly appreciated.[/COLOR]  (Aside:  sda1 = Win recovery partition & sda6 = WinXP partition that I believe Vista needs)
```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *         81,920    20,561,919    20,480,000   7 NTFS / exFAT / HPFS
/dev/sda2          20,561,920   375,694,984   355,133,065   7 NTFS / exFAT / HPFS
/dev/sda3         375,695,360   474,785,791    99,090,432  83 Linux
[COLOR="red"]/dev/sda4         474,785,829   488,408,129    13,622,301   f W95 Extended (LBA)
[/COLOR]/dev/sda5         474,789,888   483,153,903     8,364,016  82 Linux swap / Solaris
/dev/sda6         483,155,968   488,394,751     5,238,784   c W95 FAT32 (LBA)

[COLOR="Red"]/dev/sda4 ends after the last sector of /dev/sda[/COLOR]

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        AAB6D921B6D8EEB7                       ntfs       RECOVERY
/dev/sda2        2C6EDB496EDB0B0A                       ntfs       OS
/dev/sda3        c8b8a260-2aee-41f7-9817-bb9fd81ae480   ext4       
/dev/sda5        a81f6651-2ce6-494d-be30-9d5d5a00b6d3   swap       
/dev/sda6        F612-BE90                              vfat       MEDIADIRECT
/dev/sr0                                                iso9660    Ubuntu 12.04 LTS i386


```

---

### Post by oldfred on 2012-10-22
Testdisk does this as does some Windows partitioning tools. With testdisk it is something to do with it using the ancient CHS system and rounding & it has to round up and then is using a number too large.

This is one of the ways to fix it.

First backup partition table, and copy to another device.
sudo sfdisk -d /dev/sda > parts_sda.txt


Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by mph3 on 2012-10-23
Thank you, oldfred!  I was able to use fixparts and then use gParted to re-size.  A question before I mark this solved as I'm confused by 1 thing.  When running fixparts, it stated "extended partitions are not displayed", and this was sda4 for me.  After running it, gParted worked, so I assumed I would see no partition start/end overlap.  But sda4 does appear to still occupy the same space as sda5 & sda6.  Is this normal & just my lack of understanding of extended partitions?

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       81920    20561919    10240000    7  HPFS/NTFS/exFAT
/dev/sda2        20561920   184401919    81920000    7  HPFS/NTFS/exFAT
/dev/sda3       184401920   474783743   145190912   83  Linux
/dev/sda4       474789887   488394751     6802432+   f  W95 Ext'd (LBA)
/dev/sda5       474789888   483153903     4182008   82  Linux swap / Solaris
/dev/sda6       483155968   488394751     2619392    c  W95 FAT32 (LBA)

```

---

### Post by oldfred on 2012-10-23
Originally MBR(msdos) only allowed 4 primary partitions. They soon realized that was not enough and allowed one and only one primary partition to be an extended partition that is just a container for logical partitions. 

So yes the extended partition has to be the same (or larger) than all the logicals inside it.

[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)


But there is a new partitioning type gpt(GUID) that Linux can use, but Windows only uses with the new UEFI booting that is replacing BIOS. All partitions are primary and there is no extended or logical partitions.

---

