---
title: "gparted can't see my FAT disk"
date: 2008-02-18
forum: General Help
---

### Post by geo909 on 2008-02-18
Hello everybody.
I have a small 256MB MP3 Player formatted in FAT:

```
jorge@jorge-desktop:~$ fdisk -l
Note: sector size is 2048 (not 512)

Disk /dev/sdc: 268 MB, 268435456 bytes
16 heads, 57 sectors/track, 143 cylinders
Units = cylinders of 912 * 2048 = 1867776 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         144      261056    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(755, 15, 0) logical=(143, 2, 29)
Partition 1 does not end on cylinder boundary.
jorge@jorge-desktop:~$ 

```

The thing is that when I open gparted, it sees the disk as unallocated space, about 60 MB or so:


[IMG][[IMG]http://www.imageshack.gr/files/azet2abx8fjennakfoxv.png[/IMG]](http://www.imageshack.gr/view.php?file=azet2abx8fjennakfoxv.png)[/IMG]

That's so strange..
Anyone has any ideas how could I fix that?

---

### Post by geo909 on 2008-02-19
*bump*

---

### Post by geo909 on 2008-02-19
bum-doo-dilly-bump

---

### Post by geo909 on 2008-02-20
ANybody?:(

---

