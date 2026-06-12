---
title: "Will tune2fs -j mess with any of my data?"
date: 2007-10-20
forum: General Help
---

### Post by dpar on 2007-10-20
My /home partition is ext2 (I won't go into how it got that way:oops:)
If I use ```
tune2fs -j
``` to convert it to ext3, will it mess with any of the data on the partition??

---

### Post by ubernoob on 2007-10-20
no, but it is best if the home partition isn't mounted while you do it. Take a look at the man page:
man tune2fs

---

### Post by der_joachim on 2007-10-21
Be sure to edit /etc/fstab as well.

---

