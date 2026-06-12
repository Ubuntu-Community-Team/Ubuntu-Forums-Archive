---
title: "chattr &amp; lsattr on reiserfs?"
date: 2007-10-13
forum: General Help
---

### Post by wormser on 2007-10-13
Is it possible to make lsattr work on reiserfs?  I was getting the error below and looked at the man page.  It appears that chattr and lsattr are only for ex2 file systems.  In my searches I have found posts that mention a patch for reiserfs but I cannot find it.

> $ chattr +a test.chattr 
chattr: Inappropriate ioctl for device while reading flags on test.chattr

---

### Post by Pumalite on 2007-10-13
[http://osdir.com/ml/file-systems.reiserfs.general/2003-07/msg00159.html](http://osdir.com/ml/file-systems.reiserfs.general/2003-07/msg00159.html)
[http://osdir.com/ml/file-systems.reiserfs.general/2003-07/msg00157.html](http://osdir.com/ml/file-systems.reiserfs.general/2003-07/msg00157.html)

---

