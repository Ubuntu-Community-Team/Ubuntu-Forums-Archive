---
title: "cfdisk fail"
date: 2013-08-01
forum: General Help
---

### Post by e1ektrob0y on 2013-08-01
I just got a new external hard disk. I decided to try using cfdisk. I'm not sure what has gone wrong but the disk doesn't seem to mount properly. I deleted the existing partition that it came with, created a new primary partition of the type W95 FAT32 and then pressed 'write', then 'quit' from cfdisk. This is what fdisk -l says now. What have I done wrong? 

```
Disk /dev/sdc: 500.1 GB, 500074283008 bytes
255 heads, 63 sectors/track, 60797 cylinders, total 976707584 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004a183

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   976707583   488353760+   b  W95 FAT32
```

---

### Post by sudodus on 2013-08-01
I don't see anything wrong with the drive partition table. Gparted and other modern tools leave the first megabyte free so the first partition starts at sector 2048 (of size 512 bytes). This is to leave more space than before for drive administration like boot loaders etc.

Was it possible to boot the drive before?

Have you tried to boot it manually with terminal window commands?

```
 sudo mount -t auto /dev/sdc1 /mnt
```

---

### Post by e1ektrob0y on 2013-08-01
It was possible to mount it when i got it out of the box. When i try
```
sudo mount -t auto /dev/sdc1 /mnt
```
i get 
```
mount: you must specify the filesystem type
```

---

### Post by sudodus on 2013-08-01
So there is a problem with the interface of the external box. Probably it works / mounts in Windows. Try that if you haven't! If it does not work in Windows it's bricked.

Of course you can try to specify the file system, vfat for fat32 (instead of auto), but I doubt it will work:

```
sudo mount -t vfat /dev/sdc1 /mnt
```

Many external boxes work without problems with linux. I have Akasa and IcyBox, which work well will linux as well as Windows using USB as well as eSATA.

---

### Post by e1ektrob0y on 2013-08-01
Using gparted the disk now works. I'm more interested in what it is that i did wrong using cfdisk in the first place. When I opened it with gparted it couldn't read the file system but it deleted the partition and created a new fat32 partition. I'd like to know how to achieve this with cfdisk though. Oh well :(

---

### Post by sudodus on 2013-08-01
I don't know. The only unusual thing (or difference to that made with gparted), that I see is the start position of the first partition, 63 vs. 2048. Maybe this is assumed or necessary is combination with the firmware of the external box.

I have one internal HDD, that starts at sector 63, and it works for me, it is *not wrong*.

*Edit*: I think you can decide manually the start and end position of the partition. Try with 2048 for the start position. Then you may succeed with cfdisk. Anyway, this is possible with fdisk, so I think it is possible with cfdisk too.

---

### Post by davidsrsb on 2013-08-01
Over the years I have had a few disks that fdisk works fine with, but cfdisk fails

---

