---
title: "Need to mount hd using Ubuntu Live: wrong filesystem"
date: 2007-01-23
forum: General Help
---

### Post by DigitalDingo on 2007-01-23
Since I trashed my Ubuntu Edgy installation I'm trying to get into the hard drive through Ubuntu Edgy Live cd. Here's the fdisk output:```
$ sudo fdisk -l

Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       11784    94654948+  83  Linux
/dev/hda2           11785       12161     3028252+   5  Extended
/dev/hda5           11785       12161     3028221   82  Linux swap / Solaris

```
Here's what I do to mount:```
$ sudo mkdir /mnt/hda2
$ sudo mount -t ext3 /dev/hda2 /mnt/hda2
mount: wrong fs type, bad option, bad superblock on /dev/hda2,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
and here's the output from dmesg | tail:```
$ dmesg | tail
[17180704.688000] EXT3-fs: unable to read superblock
[17180711.412000] attempt to access beyond end of device
[17180711.412000] hda2: rw=0, want=4, limit=2
[17180711.412000] EXT2-fs: unable to read superblock
[17180713.596000] attempt to access beyond end of device
[17180713.596000] hda2: rw=0, want=4, limit=2
[17180713.596000] EXT3-fs: unable to read superblock
[17181021.400000] attempt to access beyond end of device
[17181021.400000] hda2: rw=0, want=4, limit=2
[17181021.400000] EXT3-fs: unable to read superblock

```
Doesn't look pretty...:(  Is there any way I can reach and backup my old files before reinstalling Ubuntu?

---

### Post by flixer on 2007-01-23
I would recommend [Trinity Rescue Kit]("http://trinityhome.org/Home/index.php?wpid=1&front_id=12"). It's the best I know.

---

### Post by DigitalDingo on 2007-01-23
Thank you very much. I'll try that in a minute!

---

