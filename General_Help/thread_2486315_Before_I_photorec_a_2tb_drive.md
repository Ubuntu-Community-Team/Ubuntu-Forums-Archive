---
title: "Before I photorec a 2tb drive"
date: 2023-04-26
forum: General Help
---

### Post by Evil Wayz on 2023-04-26
Anyone know if they make an xfs_undelete for Ubuntu? They make it for Arch.  Not sure if I could comple it or not.

I already tried testdisk but it won't list the files and I don't seem to be able to explain to the good folks at cgsecurity that its a single disk not a raid and thats the disk not a partition.

---

### Post by TheFu on 2023-04-26
Many data recovery tools don't work without partitions.  This is one reason why it is a "best practice" to always have a partition table on all storage.

The easy answer is to just wipe the drive, start over completely, this time with a GPT, then restore from your backups.  If you don't have backups, I don't know any solution. Sorry.

---

### Post by Evil Wayz on 2023-04-26
To flesh this out, i can mount the drive and theres the two folders that are supposed to be on it.  They are empty and everything is in the hidden lost and found folder.

---

