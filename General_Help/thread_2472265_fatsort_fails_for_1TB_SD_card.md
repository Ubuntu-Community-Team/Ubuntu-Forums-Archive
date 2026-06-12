---
title: "fatsort fails for 1TB SD card"
date: 2022-02-22
forum: General Help
---

### Post by jvglynnjr on 2022-02-22
I have used *fatsort* successfully on several SD cards (8 GB and 16 GB) but when I try to use it on a 1 TB card I get the following error message:

```
check_bootsector: Sectors have a size of zero!
read_bootsector: This is not a FAT boot sector or sector is damaged!
openFileSystem: Failed to read boot sector!
sortFileSystem: Failed to open file system!
main: Failed to sort file system!
```

 When I run *sudo fsck.vfat /dev/mmcblk0p1 *I get
```
fsck.fat 4.1 (2017-01-24)
Logical sector size is zero.
```

My understanding was that *fatsort* can handle exFAT. Is this not the case? There doesn't appear to be anything functionally wrong with the 1 TB SD card. I can access all the files just fine, but I want media players to play them in the correct order.

---

