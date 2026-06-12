---
title: "ddrescue (dd_rescue) as a Ghost 2003 / Imaging tool replacement?"
date: 2006-10-27
forum: General Help
---

### Post by sefs on 2006-10-27
Hi all just some quick questions to get some clarifications.

Scenario:
I currently use Ghost 2003 to do backups to my computer system (ubuntu 6.06 dapper).

I use it because:
1) it supports ext3
2) it compresses the image backup
3) it can split the size into chunks (for easy burning to CD/DVD
4) it runs from a simple boot disk or CD with absolutely no hassle.
5) it can image an entire hard drive (with multiple partitions intact) and you can restore this image onto another hard drive or partition.
6) it can image simply a partition which can be restored to a hardrive or partiton.

Eventually as linux progresses Ghost 2003 will probably not be able to support the advances in the file system, hence I would like very much to replace it.

I have been looking at ddrescue (dd_rescue?)

1) is ddrescue the same program as dd_rescue)

2) can ddrescue image just a partition (like Ghost).
3) can ddrescure image an entire hard drive (like Ghost).
4) I understand compression can be done with tar so thats good.
5) Really important can it split files into manageable chunks as it does its work.

Is this a good replacement for Ghost 2003.

Thanks.

---

### Post by frodon on 2006-10-27
Check partimage : [http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

It's a well know equivalent for linux, it's easy to use and powerful.

---

### Post by sefs on 2006-10-27
Gracias!

---

### Post by sixhat on 2008-07-17
ddrescue and dd_rescue are 2 different programs. Both try to use dd to recover partitions, but they don't share code. ddrescue is the GNU version and should be used.

---

### Post by frodon on 2008-07-17
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=78059&stc=1&d=1216310936[/IMG]

closed

---

