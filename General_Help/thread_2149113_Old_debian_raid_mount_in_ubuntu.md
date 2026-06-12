---
title: "Old debian raid mount in ubuntu?"
date: 2013-05-27
forum: General Help
---

### Post by Xencored on 2013-05-27
Howdy all, 

Let me start of by saying I am new to linux and still learning :D so please bare with me.

Now my problem.

I used to have debain install on my home server and ive now moved to the xbmc build of ubuntu (xbmcbuntu)
I had a 6TB raid mounted as /home/media on the old debian setup. (which is quite full and I don't want to loss this data (2tbx3 raid 0)) I am waiting on a few more drives to set up raid 5 to be safe but this is a tale for some other day.

Here is my ```
fdisk-l 
```

```
fdisk -l

Disk /dev/sda: 80.0 GB, 80025280000 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156299375 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a9435


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   139526143    69762048   83  Linux
/dev/sda2       139528190   156297215     8384513    5  Extended
/dev/sda5       139528192   156297215     8384512   82  Linux swap / Solaris


Disk /dev/sdb: 2000.4 GB, 2000397852160 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907027055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00006463


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  3907024895  1953511424   fd  Linux raid autodetect


Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0003e7d0


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  3907028991  1953513472   fd  Linux raid autodetect


Disk /dev/sdd: 2000.4 GB, 2000397852160 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907027055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c4a5b


   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048  3907024895  1953511424   fd  Linux raid autodetect



```

Can I still use my old raid on ubuntu ?
If so can someone help me out here please as am scared I will mess up and loss all the data on the drives :(

Cheers

---

