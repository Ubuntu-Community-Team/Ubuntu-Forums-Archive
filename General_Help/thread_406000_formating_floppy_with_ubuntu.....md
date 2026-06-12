---
title: "formating floppy with ubuntu...."
date: 2007-04-10
forum: General Help
---

### Post by Mia_tech on 2007-04-10
is it possible to format a floppy in ubuntu that will not be recognized by windows?

Thanks

---

### Post by anaconda on 2007-04-10
yes it is.. just use ex2 filesystem, or reiserfs.

more info:
man mke2fs

but basically all you would have to do is:
sudo mke2fs /dev/fd0

If I remember correctly that floppy drive is fd0.. That command would destroy everything on the disk and create a new ext2 filesystem to it. (same than format in windows..)


(actually ext2 is readable from windows, but then you would have to install ext2 drivers for windows..)

---

