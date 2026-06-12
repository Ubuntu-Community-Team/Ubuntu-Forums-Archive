---
title: "Nautilus showing funny volume"
date: 2007-09-25
forum: General Help
---

### Post by youbaba on 2007-09-25
Hi.

Because of some prob which shouldn't be of any interest here I had to delete my root partition today. Ofc I  had made a backup of the contents before and copied them over to the new root partition. 
Basically everything went well, besides one minor flaw: Nautilus is now showing some "8.8 GB Volume" next to my CD-Rom drives, FAT partitions, etc. Guessing from the size this should be my root partition. Funny thing is that the icon is showing "not mounted", yet it definitely IS mounted (how would I have managed to come here otherwise :-P).

I guess that icon shouldn't be there at all, as there are also none for my other partitions (home, boot, etc).

How do I get rid of it again?

---

### Post by youbaba on 2007-09-25
It has nothing to do with the user settings, I've created a new user and checked :-/

---

### Post by notwen on 2007-09-25
Open up a terminal and type this, then paste the output back here.

```
sudo fdisk -l
```

---

### Post by youbaba on 2007-09-25
```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
16 heads, 63 sectors/track, 155061 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       22350    11264368+   c  W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.
/dev/hda2           22361       24225      939802+  82  Linux swap / Solaris
Partition 2 does not end on cylinder boundary.
/dev/hda3           24226       42633     9277537+  83  Linux
Partition 3 does not end on cylinder boundary.
/dev/hda4           42633      155056    56661255    c  W95 FAT32 (LBA)
Partition 4 does not end on cylinder boundary.

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
16 heads, 63 sectors/track, 158816 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1      158816    80043232+  83  Linux
```

---

### Post by youbaba on 2007-09-25
I guess it's some HAL problem but the HAL guys sent me here (bug in your distro).

---

### Post by youbaba on 2007-09-27
halp?

---

