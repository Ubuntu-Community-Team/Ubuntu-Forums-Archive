---
title: "Mounting partitions help."
date: 2007-03-01
forum: General Help
---

### Post by venator260 on 2007-03-01
Alright, so I followed the tutorial on psychocats.com about mounting drives. 

I have a FAT32 partition on the same hard drive as Ubuntu. I edit the fstab file, by putting this in


```
# /dev/hdd4
UUID=E8E5-8028   /fat_files vfat iocharset=utf8,umask=000 0 0

```

Note that the partition I want to mount is indeed hdd4 and that directory does exist.

I then enter the sudo mount -a command, and get this error.

```
mount: /dev/disk/by-uuid/E8E5-8028: can't read superblock

```

I've had this drive mounted on my 2 installs of 6.06. However, that decided that it wouldn't let me log on, so I formated my Linux partition and upgrated to 6.10 about an hour ago.

---

### Post by taurus on 2007-03-01
What's the output of this command from a terminal?

```
sudo fdisk -l
```

Perhaps you need to use this in /etc/fstab instead.

```
/dev/hdd4   /fat_files   vfat   iocharset=utf8,umask=000   0   0
```

---

### Post by venator260 on 2007-03-01
```
venator260@venator260-desktop:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1           5       40131   de  Dell Utility
/dev/hda2   *           6        4328    34724497+   7  HPFS/NTFS
/dev/hda3            4329        4862     4289355   db  CP/M / CTOS / ...

Disk /dev/hdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd2   *        8013        9686    13446405   83  Linux
/dev/hdd3            9687        9729      345397+   5  Extended
/dev/hdd4               1        8012    64356358+   c  W95 FAT32 (LBA)
/dev/hdd5            9687        9729      345366   82  Linux swap / Solaris

Partition table entries are not in disk order

```

I edited my fstab according to taurus's suggestion, and got this

```
venator260@venator260-desktop:~$ sudo mount -a
[mntent]: line 13 in /etc/fstab is bad
```

The fstab line in question looks like this(in case I screwed up somehow):

```
UUID=E8E5-8028   /dev/hdd4   /fat_files   vfat   iocharset=utf8,umask=000   0   0

```

---

### Post by yabbadabbadont on 2007-03-01
```
UUID=E8E5-8028   /dev/hdd4   /fat_files   vfat   iocharset=utf8,umask=000   0   0
```
Should be:
```
/dev/hdd4   /fat_files   vfat   iocharset=utf8,umask=000   0   0
```

---

### Post by venator260 on 2007-03-01
And now it spits out the error, once again:

> venator260@venator260-desktop:~$ sudo mount -a
mount: /dev/hdd4: can't read superblock


Thanks for your help so far folks.

---

### Post by taurus on 2007-03-01
I recommend you boot XP and scan or defrag /dev/hdd4 first to fix whatever the problem there is with /dev/hdd4.

---

