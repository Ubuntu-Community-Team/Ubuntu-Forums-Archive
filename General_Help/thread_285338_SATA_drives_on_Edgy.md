---
title: "SATA drives on Edgy"
date: 2006-10-26
forum: General Help
---

### Post by WiseElben on 2006-10-26
Hi, it seems that Edgy isn't reading my other SATA drives (already formatted with NTFS and FAT32 from a previous install). Gparted simply hangs at "Scanning all devices..." My fstab doesn't have the other drives too. Actually, gparted was hanging during the LiveCD install too.

Any suggestions? Thanks.

EDIT: Ah, I found this thread: [http://ubuntuforums.org/showthread.php?t=263123](http://ubuntuforums.org/showthread.php?t=263123)
I'll see what happens.

EDIT 2: So I can view the partitions using <sudo gparted /dev/sda /dev/sdb>, but I can't access sdc for some reason. It is using the FAT32 filesystem. Also, though I can view these partitions, I can't access them.

---

