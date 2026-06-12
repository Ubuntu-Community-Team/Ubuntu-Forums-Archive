---
title: "How to delete partitions via the command line?"
date: 2007-05-21
forum: General Help
---

### Post by 67GTA on 2007-05-21
What command can I use to delete a partition seen using fdisk via the command line?

---

### Post by yabbadabbadont on 2007-05-21
parted

"man parted" for details.

---

### Post by Nikron on 2007-05-21
Or you can do "sudo fdisk <targe drive>".  Remember to umount target drives.

---

