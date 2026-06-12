---
title: "HDD space problem"
date: 2008-04-26
forum: General Help
---

### Post by ipatec on 2008-04-26
I have an WD 120 GB HDD but when I look in disk usage analyzer it shows me:
"Total filesystem capacity:216 GB"
How can I solve this?

---

### Post by ajmorris on 2008-04-26
hi there,
i assume you meant "**1**16GB" space, not 216.
This is not fixable, this is simply because of the way Hard Disk manufacturers make their Hard Disks. A Giga Byte is determined by 1024x1024x1024 bytes. (in other words, hard disk space is a factor of 1024 not 1000.)  However, although this 1024 method is the correct one, Hard Disk manufacturers use a 1000x1000x1000 byte method, yielding less overall Hard Disk than you are supposed to have.

AJ

---

### Post by lonniehenry on 2008-04-26
No, he means 216 and it is caused by adding the regular space and the amount from gvfs-fuse-daemon.  It is part of the mounting for gvfs. It happens to me also.

---

### Post by Vivaldi Gloria on 2008-04-26
I am sure that this problem was discussed in a thread not so long ago and there was a solution given there. But I don't remember it. Anyone?

---

### Post by ipatec on 2008-04-26
I didn't made a mistake when I said 216 GB... My HDD capacity is 120 GB but there sais that filesystem capacity is 216 GB...

---

### Post by OMRebel on 2008-04-29
I have a similiar problem.  I have a 80 GB HD, but Disk Usage Analyzer says 141.8 GB.  I'm running this on an Inspiron 1501.

---

### Post by ipatec on 2008-04-30
I also have Inspiron 6400 and I know that's alsmost the same with 1501...

---

