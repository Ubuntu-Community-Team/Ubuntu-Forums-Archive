---
title: "file system to use for a shared windows/linux partition"
date: 2007-03-03
forum: General Help
---

### Post by Phantom784 on 2007-03-03
I'm going to be installing a new system soon, and I want it to be dual boot Windows and Ubuntu.  In addition to the partitions for Windows and Linux, I want to have a partition that they both can access.  Which would be the best to use?  I will probably spend most of my time on Ubuntu, and only boot into Windows for gaming or anything else that doesn't work on Linux.

*ext 2/3, with windows ext2 driver
*ntfs, with Linux ntfs read/write driver
*fat32, native on both, but requires defragmentation

---

### Post by taurus on 2007-03-03
Personally, I would go with the first choice, ext3 with [http://www.fs-driver.org](http://www.fs-driver.org) for Windows.

---

### Post by djheadley on 2007-03-03
I use fat32 partitions for sharing and have not had any problems.

---

### Post by fakie_flip on 2007-03-04
When you have the ext2/ext3 volumes mounted when you get a windows virus, what happens? Your data in Linux could be destroyed from a winblows virus.

---

### Post by fakie_flip on 2007-03-04
does anyone know about explore2fs? ive heard good things about it and also that it mounts the linux partitions as read only. that would be better incase of a windows virus, so that the windows virus couldnt not destroy or corrupt what's in linux.

---

