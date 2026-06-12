---
title: "External drive permissions"
date: 2008-04-11
forum: General Help
---

### Post by vasiliymeshko on 2008-04-11
I have an external usb hard drive (NTFS fromated) I want to set permissions so that only root can have write access to root level of the drive, and regular users can only read/write to existing folders only (no write access to root level) Is this possible to do on Ubuntu / NTFS file system?

---

### Post by mmc on 2008-04-12
yip - simplest way to achieve this is to use existing files permissions & not look to do anything fancy with the NTFS stuff, 

so just look to create 2 new mount points,
  [1] root owned & mounting the root of the partition
  [2] user owned & mounting the sub-directories of the partition.


take a look at mount points & NTFS mounting on the wiki here -> [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions) & here -> [https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

hth

mmc.

---

