---
title: "GParted messed up NTFS partition"
date: 2017-02-05
forum: General Help
---

### Post by wintergrascph on 2017-02-05
Hey!

I tried to resize an NTFS partition, GParted threw and error and now the NTFS partition is broken.

Here are the GParted logs: [http://paste.ubuntu.com/23937710/](http://paste.ubuntu.com/23937710/)

Thank you!

---

### Post by TheFu on 2017-02-05
I learned long ago to perform file system stuff using the OS that is best for that file system. Why?  There are many different types of NTFS partitions that only Windows can handle.  If they are "simple" partitions, gparted should handle them correctly, provided they are closed and not left open by Windows or having zero corruption. In the log, corruption is show.  By that point, it was probably too late.

> Schedule chkdsk for NTFS consistency check at Windows boot time ...
really says it all.
So ... boot into Windows and use Windows tools to try and fix that partition.

---

