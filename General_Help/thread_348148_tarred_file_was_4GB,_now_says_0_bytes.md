---
title: "tarred file was 4GB, now says 0 bytes"
date: 2007-01-28
forum: General Help
---

### Post by davidshere on 2007-01-28
A few days ago, I tarred a directory to a file from the command line:

tar cfvz videos.tar videos

and the videos.tar file was 4GB.  This is on a vfat partition.  I returned to the file today to transfer it and it now has a file size of 0 bytes and will not uncompress.

Suggestions?

---

### Post by taurus on 2007-01-28
Vfat/fat32 cannot handle files over 4GB.

---

### Post by davidshere on 2007-01-28
Ah.  Thanks.

I was thinking about changing away from vfat for this partition, but it's my main data partition, so I want to be able to read it from the windows side too.

Oh well.  Lesson learned.  4GB of data down the tubes.

---

### Post by taurus on 2007-01-28
Windows can read and write to ext2/ext3.

[http://www.fs-driver.org](http://www.fs-driver.org)

---

