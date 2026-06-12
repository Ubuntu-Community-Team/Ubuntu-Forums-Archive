---
title: "Update removed Windows from grub"
date: 2007-11-01
forum: General Help
---

### Post by serlex on 2007-11-01
Havent used my ubuntu for 3-4 months, thought i update it (144 updates) installed the updates, restarted the machine, my windows partition is missing from the grub! i dont remeber what partition number windows was. Any ideas on how i can get my windows back? :'(

Thanks

---

### Post by Saubazi on 2007-11-01
Look what partition it is on for example sudo fdisk -l
I get for example:


   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       10010    80405293+   7  HPFS/NTFS


Since my two first devices /dev/hda and /dev/hdb are cdroms I have:
title           Windows 2000
root            (hd0,0)
savedefault
makeactive
chainloader     +1

entry in grub/menu.lst - here I don't actually know why not hd(2,0) or why it works without map options but it does...

---

### Post by serlex on 2007-11-01
grr, I'm going to go crazy!!!

here is  sudo fdisk -l

```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         924     7421998+  83  Linux
/dev/hda2             925        1049     1004062+  82  Linux swap / Solaris
/dev/hda3            1050        9729    69722100    7  HPFS/NTFS

```

looks like windows is in hda3, so i did sudo fdisk -l /dev/hda3

```

Disk /dev/hda3: 71.3 GB, 71395430400 bytes
255 heads, 63 sectors/track, 8680 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/hda3p1   ?       13578      119522   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/hda3p2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/hda3p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/hda3p4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.
```

and the put it in menu.lst
```
title 		Microsoft
root 		(hd0,3)
makeactive
savedefault
chainloader +1

```

comes up with "no such partition", i really can not afford to loose my windows partition :(

---

### Post by Saubazi on 2007-11-01
Yeah well grub is a number of it's own you need to substract one from your entries try (hd0,2) for /dev/hda3...

---

### Post by serlex on 2007-11-01
ahh

Thank you Saubazi! it is working

---

