---
title: "Can I read my Ubuntu files from my Windows partition?"
date: 2007-02-14
forum: General Help
---

### Post by dnccnd on 2007-02-14
Hallo!

I have read a few threads about reading and writing between Windows and Ubuntu partitions. I can read my Windows partition from Ubuntu, but I was wondering whether it is possible to do the opposite... reading my files on the Ubuntu partition from Windows.

---

### Post by charl.ie on 2007-02-14
Yes you can.

[http://www.fs-driver.org/]("http://www.fs-driver.org/")

This gives you a filesystem drive for ext2 and ext3 filesystems in windows, so your partion will appear as another drive letter.

---

### Post by bash on 2007-02-14
Yes you can. There exists a little handy driver for windows which lets you read and write from ext2/ext3 partitions. But don't forget it treats ext3 partitions as ext2, so no journaling.

The driver can be found here: [http://www.fs-driver.org/](http://www.fs-driver.org/)

/edit:

Ah cwap someone was quicker :D

---

### Post by dnccnd on 2007-02-18
Sorry for my late reply!

It works perfectly, thank you a lot!

---

