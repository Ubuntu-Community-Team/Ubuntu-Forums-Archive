---
title: "mounting ntfs image from ddrescue"
date: 2012-12-03
forum: General Help
---

### Post by Bobscrachy on 2012-12-03
I am getting stumped on the syntax for mounting this ntfs file partition I made from a failing hard drive. 

```

Disk image: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe0c5913d

Device Boot      Start         End      Blocks   Id  System
image1              63    40965749    20482843+  1c  Hidden W95 FAT32 (LBA)
image2   *    40965750   353525885   156280068    7  HPFS/NTFS/exFAT
image3       353527808  1250260991   448366592    f  W95 Ext'd (LBA)
image5       353529856  1250260991   448365568    7  HPFS/NTFS/exFAT

```

Here is what im using, that i know is good. 

```
sudo mount -o loop,offset=229563170816 image /mnt
```

This is what i get when I try and put the filesystem option in. 

```
/media/B2402CAC402C796D/mnt$ sudo mount -t ntfs -o loop,offset=229563170816 image /mnt
[sudo] password for swrd: 
NTFS signature is missing.

```

Is there anyone here who can help, or who has done this before?

---

### Post by Bobscrachy on 2012-12-04
```

/media/B2402CAC402C796D/mnt# mount -t ntfs-3g -o loop,offset=181007286272 jimbob /mnt


```


I tried changing the image name thinking that I might not be calling the right file. 

Then I discovered that I wasn't calling the right ntfs type, so I plugged in ntfs-3 and it mounted right on up. I thought I would post this if anyone else had the same problem.

---

