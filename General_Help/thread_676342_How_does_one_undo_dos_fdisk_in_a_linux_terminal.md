---
title: "How does one undo dos fdisk in a linux terminal"
date: 2008-01-23
forum: General Help
---

### Post by ele_mugv on 2008-01-23
How does one undo dos fdisk in a linux terminal...or some sort of a recovery tool

---

### Post by bodhi.zazen on 2008-01-23
you can use the try either testdisk (it is in the Ubutnu repos) or fdisk directly.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)


		How to testdisk : [http://www.debian-administration.org/articles/420](http://www.debian-administration.org/articles/420)

fdisk, in Linux, does not format the partitions, so you can usually un-do the changes, BUT you need to know (or guess) the previous disk geometry.

---

