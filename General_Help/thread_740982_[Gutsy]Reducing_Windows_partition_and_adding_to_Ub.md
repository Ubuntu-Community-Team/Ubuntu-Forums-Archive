---
title: "[Gutsy]Reducing Windows partition and adding to Ubuntu?"
date: 2008-03-31
forum: General Help
---

### Post by Woodtile on 2008-03-31
I have both 7.10 and Windows XP installed on one hard disk. I intend to reduce the size of the XP partition and add the freed-up space to 7.10's partition. Is this possible without reinstalling?

---

### Post by lswest on 2008-03-31
Yup, you can (after defragmenting XP) resize the ntfs partition using either a gparted liveCD, or gparted off the Ubuntu LiveCD (from system-->administration-->Partition Manager), or even install gparted into your installed Ubuntu to do it from. ```
sudo apt-get install gparted
```  then you can resize Ubuntu using the same method (right-click-->resize).  However, you **can not** do it from your installed Ubuntu (unlike the XP resizing) because the system files of Ubuntu are in use, and cannot be moved.

Oh, and a word of warning: Resizing Ubuntu might take a little bit longer than you expect, because it first has to grow the ext3 partition, and then grow the actual filesystem (the "/" if you will) without damaging files.  So don't worry if it seems slow.

---

