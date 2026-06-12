---
title: "VeraCrypt: how to force my system to see my hdd as 4096-byte?"
date: 2019-03-17
forum: General Help
---

### Post by justcurious on 2019-03-17
I'd like to create a VeraCrypt volume on my 4TB external hdd with 50GB  of outer volume and the rest hidden. However, during the set up process I  get the following error message: 

[ATTACH=CONFIG]282808[/ATTACH]

I **don't want to divide** it into two partitions, so I checked *sudo fdisk -l /dev/sdc* to find out about the sector size:

```
Disk /dev/sdc: 3.7 TiB, 4000787029504 bytes, 7814037167 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 33553920 bytes
Disklabel type: gpt
Disk identifier: 57DF69GQ-C896-R557-EE98-54GF68GF7898

Device     Start        End    Sectors  Size Type
/dev/sdc1   2048 7814035455 7814033408  3.7T Linux filesystem
```

How to force my system and VeraCrypt to see the hdd as 4096?

---

