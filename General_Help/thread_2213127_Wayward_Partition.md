---
title: "Wayward Partition"
date: 2014-03-25
forum: General Help
---

### Post by PJs Ronin on 2014-03-25
I have a HD (SDA) that contains my production system, Saucy, on a dedicated partition.   On the same HD I have other Linux partitions where I try and learn things about Linux, Trusty and the universe.   All my data resides on a seperate HD, SDB.

Here is the info on SDA:```
wayne@saucy:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00031b47

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *     1957886   329641983   163842049    5  Extended
/dev/sda3       517578752   956293119   219357184   83  Linux
/dev/sda4       956293120   976773119    10240000   82  Linux swap / Solaris
/dev/sda5         1957888    42917887    20480000   83  Linux
/dev/sda6        42919936    83880873    20480469   83  Linux
/dev/sda7        83881984   124842921    20480469   83  Linux
/dev/sda8       124844032   165791297    20473633   83  Linux
/dev/sda9       165793792   206754729    20480469   83  Linux
/dev/sda10      206757888   247717887    20480000   83  Linux
/dev/sda11      247719936   288680873    20480469   83  Linux
/dev/sda12      288681984   329641983    20480000   83  Linux
```
and a partial screen print using Gparted:
[ATTACH=CONFIG]251443[/ATTACH]

As can be seen (or not seen) there is no SDA1.   There used to be, but for some reason I managed to "get rid of  it" and am now left with nearly a Gb of space at the beginning of the drive.   This is something I would like to clean up.

What are the suggestions for my best course of action to recover/remove/use that first Gb of space?   I understand that by leaving things alone no harm, no foul... but I would prefer to have things orderly.

---

### Post by oldfred on 2014-03-25
I would not worry about it.
Sometimes moving things around can create more issues. You would have to move extended left, then move sda5 left. If do not like moving partitions left as all data has to be copied and any issue like power failure or other interruption will corrupt data. Good backups are required.

You still can expand extended partition right to use the 89GB unallocated and create new logical partitions, so you still have room if needed.

---

### Post by PJs Ronin on 2014-03-25
Ty oldfred
I thought perhaps I was overlooking something simple.

---

