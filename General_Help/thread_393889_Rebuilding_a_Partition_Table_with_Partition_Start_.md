---
title: "Rebuilding a Partition Table with Partition Start and End Info"
date: 2007-03-26
forum: General Help
---

### Post by 23meg on 2007-03-26
I have a 120GB external USB disk in my hands whose partition table was borked. I have no idea how exactly, since the disk does not belong to me. I was told that there were two partitions on the disk: one NTFS and one EXT3, each with an approximate size of 60GB. Indeed, I used the rescue functionality of parted to rescue the NTFS partition; it's intact and all data is accessible. 

Knowing where the NTFS partition begins and ends, I should be able to put the start and end positions of the EXT3 partition, which occupied the rest of the disk, into the partition table, but how exactly should I go about doing this? Should I use parted, or fdisk, and how exactly?

Here is the partition information:

```
$ sudo fdisk -u -l /dev/sdb

Disk /dev/sdb: 120.0 GB, 120034124288 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441649 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1             352   123849022    61924335+   7  HPFS/NTFS

```

I've already tried to locate the lost partition with gpart and testdisk; gpart can't find it, and testdisk only finds a 13GB EXT3 partition, when the correct size should be about 60GB. I suspect it's just the remnants of an old partition that was deleted, since it also won't let me browse its contents after analyzing (with a corrupt filesystem error).

Given that the the NTFS partition is from sector 352 to 123849022, it follows that the EXT3 partition should be from 123849023 to 234441649, right? How, if at all, can I rescue the existing data by writing this to the partition table?

---

### Post by gepatino on 2007-03-26
afaik, writing partition table data doesn't corrupt any data in the disk, as long as you don't write anything to it.

Try defining a new partition with the values you get, using the program you like. 

BUT: don't mark the partition to be formated, if such option exists. Even if the partition table doesn't show the missed partition, the data contained in it should be in the disk. Don't format or mkfs that partition, or you'll miss all the data in that partition.

once you've updated the partition table, try to mount the new partition in read only mode. If you can mount it and everything is ok, you're done. Remount it as rw if you need to modify/delete/add files.

---

### Post by 23meg on 2007-03-26
I did so, with fdisk, but the resulting partition can't be mounted. fdisk now lists the partitions as

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7710    61924335+   7  HPFS/NTFS
/dev/sdb2            7710       14593    55293761   83  Linux
```

When I try to mount the new partition, I get the usual error:

```
$ sudo mount -t ext3 /dev/sdb2 /media/usbdisk -o iocharset=utf8,umask=000
mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

The relevant dmesg | tail output:

```
[17180432.856000] VFS: Can't find ext3 filesystem on dev sdb2.
```

In GParted, the partition is listed as of an "unknown" filesystem, even though its id is seen as 83 (Linux) in fdisk. 

I'm pondering what to try next.

---

