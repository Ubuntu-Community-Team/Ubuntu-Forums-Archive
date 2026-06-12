---
title: "Target filesystem doesn't have /bin/init"
date: 2014-04-21
forum: General Help
---

### Post by yamabushi336 on 2014-04-21
Hi everyone,

I know this has been floating around the froums for a while and sorry if this is in the wrong forum board. I have been using ubuntu 14.04 ever since it came out and this hasn't happened since I installed it. What happed was I removed some bad packages and I guess ubuntu didn't like it and now I am having to run the livecd and try and fix it. I think I have found a solution but I am comfused on what disk my mount is on. ```
Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc835bc1c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848  3277886534  1638839843+   7  HPFS/NTFS/exFAT
/dev/sda3      3277883390  3907024064   314570337+   5  Extended
/dev/sda5      3277883392  3316942847    19529728   82  Linux swap / Solaris
/dev/sda6      3316944896  3907028880   295041992+  83  Linux
omitting empty partition (5)

Disk /dev/sdb: 1000.2 GB, 1000170586112 bytes
64 heads, 32 sectors/track, 953837 cylinders, total 1953458176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0068731e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            1985  1953454079   976726047+   f  W95 Ext'd (LBA)
/dev/sdb5            2048  1953454079   976726016    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 32.0 GB, 32015679488 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62530624 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x83e7520e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          32    62530623    31265296    c  W95 FAT32 (LBA)


```

the command I found is ```
es2fsck -CO -p -f -v /dev/sda(X)
```
I don't know if my mount is on sda6 or sda1 any help will be useful if all else fails I will reinstall ubuntu.

---

### Post by shadytv on 2014-04-21
It looks like your "/" is mounted on /dev/sda6

A good way to verify this for yourself is to use a tool called "gparted" which should be on the live CD.

---

### Post by yamabushi336 on 2014-04-22
The problem is solved I guess ubuntu decided to delete itself after removing those bad packages so I had to go and reformat the partitions and start fresh.

---

