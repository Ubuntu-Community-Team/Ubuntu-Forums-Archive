---
title: "ext3"
date: 2007-05-27
forum: General Help
---

### Post by atlfalcons866 on 2007-05-27
what is the maxium amount of files ext3 can i have?

---

### Post by yabbadabbadont on 2007-05-27
From the ext3 entry at wikipedia:
> The maximum number of inodes (and hence the maximum number of files and directories) is set when the file system is created. If V is the volume size in bytes, then the default number of inodes is given by V/213 (or the number of blocks, whichever is less), and the minimum by V/223. The default was deemed sufficient for most applications.
Edit: I lost the superscripts when I copied the text.  V/213 and V/223 are supposed to be V/2(to the 13th power) and V/2(to the 23rd power).

---

