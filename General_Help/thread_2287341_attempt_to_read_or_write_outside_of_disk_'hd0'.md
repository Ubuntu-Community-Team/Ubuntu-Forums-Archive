---
title: "attempt to read or write outside of disk 'hd0'"
date: 2015-07-18
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2015-07-18
I got this issue after messing with a windows 7 hdd, it did run a chkdsk operation as i missed my chance to skip it
i noticed all of my partitions on my 500gb drive aside from swap has a msftdata flag, took that off
i attached gparted screenshots below
i did manage to get it to boot, but it took far longer than it should, a few minutes
it did not drop to grub rescue, old kernels as well as recovery is affected

i ran boot repair and got this
[http://paste.ubuntu.com/11900696/](http://paste.ubuntu.com/11900696/)

Here are a couple boot charts:
 [http://i.imgur.com/FbHZajw.png](http://i.imgur.com/FbHZajw.png) (normal boot)
 [http://i.imgur.com/BHBq5yJ.png](http://i.imgur.com/BHBq5yJ.png) (current boot)
i see from this my read speed dropped to sata 1 speeds :?

```
sudo fdisk -l
[sudo] password for chad: 

Disk /dev/sda: 30.0 GB, 30016659456 bytes
255 heads, 63 sectors/track, 3649 cylinders, total 58626288 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ef58a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    40962985    20480469   83  Linux

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1   976773167   488386583+  ee  GPT
```

i have used gparted to check/repair all my partitions

---

### Post by pqwoerituytrueiwoq on 2015-07-18
i got a kerenl panic
[http://i.imgur.com/xNsppNw.jpg](http://i.imgur.com/xNsppNw.jpg)

---

### Post by pqwoerituytrueiwoq on 2015-07-18
well i think i figured it out
sata cable not fully connected, yea if SSDs supported the locking sata cables lock features that would have been great

---

