---
title: "bldid returns 8 chracters for uuid of a drive"
date: 2007-01-23
forum: General Help
---

### Post by izmeh on 2007-01-23
I'm trying to mound a 2nd drive that is formatted fat32.

I used the command blkid to get the uuid of the drive to add to my fstab. It only returns 8 characters for that drive "xxxx-xxxx". And of course it didnt work when i tried to mount the drive.

Is it possible to asign a new uuid to this drive?

```
aaron@ubuntu:~$ blkid
/dev/sda1: TYPE="ntfs" 
/dev/sda2: UUID="fb6ff4a7-ea43-4a57-b31f-fe1728322486" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="194fc7b6-6614-4595-bcea-7c9cd686c39d" TYPE="swap" 
/dev/hdd1: LABEL="SHARED" UUID="7C56-C7D0" TYPE="vfat"
```

---

