---
title: "my ubuntu partition just disappeared ....."
date: 2007-08-13
forum: General Help
---

### Post by CC_machine on 2007-08-13
ok, so here's  what happened:
my 120GB disk in my laptop is partitioned as:

sda1: ext3 for debian installation
sda2: NTFS: windows installation
sda3: extended
---sda6 ext3 for file storage
---unnallocated space (30GB)
---sda5 fat32 2GB partition that came with the machine
sda4: fat32 3GB partition that came with the machine

before, i had 2 partitions in that 30GB unallocated: a 10GB fat32 for filesharing between windows and linux(sda6), and a 20GB partition for ubuntu(sda7).

i deleted the fat32 partition. the next thing i know my ubuntu partition is gone! I know i' m not being stupid because sda6 has somehow become the ext3 partition above. what could i have done, and how could i fix it? i tried booting ubuntu in GRUB already, and it tells me the partition doesnt exist! :'(

ok so i'm beginning to think i deleted my ubuntu partition by accident. if this is the case, is there any way to "undelete" or otherwise recover the partition?

---

### Post by be4truth on 2007-08-13
It happened to me that when deleting partitions other partitions where renamed (swap files for example) I had to rewrite GRUB to get the thing going. I am afraid gone is gone when deleting a partition except you work for the secret police and have all the tools ready to recover ....
Type that into your terminal and post the output
```
 sudo fdisk -l
```

One thing you could try:
Boot into you Debian.
make a folder in /mnt

```
sudo mkdir -p /mnt/tmp
```

```
sudo mount /dev/sda6 /mnt/tmp
```

check if this is your Ubuntu. If not umount it

```
sudo umount /dev/sda6
```

Check if it is unmounted

```
mount
```

With this you mount and umount all ext3 partitions and if you don't find Ubuntu - that's it!

---

### Post by CC_machine on 2007-08-13
Device Boot      Start         End      Blocks   Id  System
/dev/sda1            5244        6564    10610932+  83  Linux
/dev/sda2   *          12        5243    42026040    7  HPFS/NTFS
/dev/sda3            6565       14201    61344202+   f  W95 Ext'd (LBA)
/dev/sda4           14202       14593     3148740   db  CP/M / CTOS / ...
/dev/sda5           13941       14201     2096451   dd  Unknown
/dev/sda6            6565        9995    27559444+  83  Linux


sda6 isnt the partition, i tried that already ...
it' s in the 30GB of "unallocated space". surely the data is still there, i just need to recreate the partition? (of course, gparted will force me to make a new filesystem ...)
what tools exist that would allow me to restore it?

---

### Post by be4truth on 2007-08-13
What I did once (and it worked) I deleted a FAT32 like you did and it changed some harddrive letters. I couldn't fix any of it really. So I recreated the fat32 and it took the same label and all other labels got changed back. Then I rescued my data.
I am not sure this was luck or not.

---

