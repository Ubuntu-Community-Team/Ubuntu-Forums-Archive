---
title: "Need data recover help - bad superblock."
date: 2006-12-26
forum: General Help
---

### Post by element on 2006-12-26
I have read through the forums, but everything that has been suggested hasnt been working for me.  Can someone help me please.  I have a bad superblock  on /dev/hdb1 or /dev/hdb and the drive wont mount.

```
**fdisk -l**
Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2330    18715693+  83  Linux
/dev/hda2            2331        2434      835380    5  Extended
/dev/hda5            2331        2434      835348+  82  Linux swap / Solaris

Disk /dev/hdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        7475    60042906    7  HPFS/NTFS


**dumpe2fs /dev/hdb1 | grep -i superblock**
dumpe2fs 1.39 (29-May-2006)
dumpe2fs: Attempt to read block from filesystem resulted in short read while trying to open /dev/hdb1
Couldn't find valid filesystem superblock.

**sudo dumpe2fs /dev/hdb | grep -i superblock**
dumpe2fs 1.39 (29-May-2006)
dumpe2fs: Bad magic number in super-block while trying to open /dev/hdb
Couldn't find valid filesystem superblock.

**sudo parted /dev/hdb p**
Disk /dev/hdb: 61.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  61.5GB  61.5GB  primary                    
Information: Don't forget to update /etc/fstab, if necessary.             

**sudo mount -t ext3 /dev/hdb /media/recovery -o nls=utf8,umask=0222**
mount: wrong fs type, bad option, bad superblock on /dev/hdb,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

---

### Post by bodhi.zazen on 2006-12-26
Is the partition ntfs ?

If so boot to windows and run chkdsk

If that fails you can try TestDisk:

[Home Page](http://www.cgsecurity.org/wiki/TestDisk)

[TestDisk & ntfs](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

---

### Post by element on 2006-12-27
Its not, its ext3.  Im not sure why it thinks it NTFS.

I tried TestDisk, but no luck.

```
TestDisk 6.4, Data Recovery Utility, June 2006
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/hdb - 61 GB / 57 GiB - CHS 119150 16 63
     Partition                  Start        End    Size in sectors
 1 P HPFS - NTFS              0   1  1 119132  12 63  120085812
Boot sector
ntfs_boot_sector: Can't read boot sector.
Bad

Backup boot sector
check_NTFS: Incorrect number of heads/cylinder 255 (NTFS) != 16 (HD)
OK

Sectors are not identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.
```

---

### Post by aysiu on 2006-12-27
Google *ddrescue*. That might help.

---

### Post by element on 2006-12-28
Thanks.  Ok, ddrescue is running right now and appears to be working.  My concern is that I dont think I have enough hard drive space to hold the .img file.  Their website says that "Also you can interrupt the rescue at any time and resume it later at the same point."  but I dont see how to do this. How do you properly stop and then restart ddrescue to pick up where I left off?  I was thinking I could stop the process, remove some files out of the img file and then proceed with the rest of the data recovery.  Is this possible? 

Oh yeah, I also tried partimage and it didnt work on the corrupt drive.

---

