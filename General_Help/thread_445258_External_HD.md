---
title: "External HD"
date: 2007-05-15
forum: General Help
---

### Post by mhamed on 2007-05-15
I have problem with my external HD sometimes ubuntu detects it automatically and othertimes no way, I can not see it. PLZ HELP

---

### Post by taurus on 2007-05-15
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by mhamed on 2007-05-16
Sorry for late response. I got;

[COLOR="Red"][B]Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3889    31238361    7  HPFS/NTFS
/dev/sda2            3890        5395    12096945    f  W95 Ext'd (LBA)
/dev/sda3            5396        9729    34812855   83  Linux
/dev/sda5            3890        5203    10554673+   7  HPFS/NTFS
/dev/sda6            5204        5395     1542208+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4864    39070048+   7  HPFS/NTFS[/B][/COLOR]

and a message says "Can not mount volume"

Note: I have another external HD (4 partitions) and just 3 of them are accessible.

---

### Post by mhamed on 2007-05-16
I think I did it but not sure if it is the right way or not using  [COLOR="Red"]**storage device manager**[/COLOR].

By the way, why it is read only?. I have tried to uncheck that option but no way.:?:

---

