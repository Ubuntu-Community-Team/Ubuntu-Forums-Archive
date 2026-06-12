---
title: "Data loss with UDF"
date: 2007-12-25
forum: General Help
---

### Post by boga on 2007-12-25
Hi, 

Am I the only one to suffer from UDF problems? Especially the data loss as a result of creating crippled files? It happends quite often with unreadable files being created with weird sizes in both DVD-RAM and DVD+RW and I've just lost a day of quite hard work thanks to it. The fstab line is is:
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

The system log contains a lot of lines like that:
Dec 25 12:25:08 boga kernel: [13000.400000] udf: udf_read_inode(ino 1031705) failed !bh
when I access the root directory of the DVD-RAM.

---

### Post by TidusBlade on 2007-12-25
I cant read UDF burnt DVDs either :( I hope somebody knows something about this...

---

### Post by boga on 2007-12-25
Mine is quite a different story. I use udftools to write to re-writable DVDs and it say in 49 cases of 50 works fine but in 1 in 50 it creates an incorrect directory entry for the file so it displays weird size and can't be read since it probably has incorrect file location.

---

