---
title: "Move root and home to new disk"
date: 2008-05-18
forum: General Help
---

### Post by petersra on 2008-05-18
I have ubuntu, / and /home partitions on one disk.  I wish to move these two partitions to a new, larger disk.  Option 1 is to install Ubuntu on the new disk and then copy /home over.  However, I would like not to have to reinstall everyting.  Is there a fool proof way of doing a disk copy, say via Ghost or something?

---

### Post by garyedwardjohnston on 2008-05-18
In Add/Remove Programs I see many backup programs.

Test them out.

---

### Post by fsmithred on 2008-05-18
Yes, there are several ways to do this, and yeah, it's a lot easier than reinstalling. The way I've done it is to have both drives in the computer. Boot live CD, partition and format the new drive, then just mount the appropriate partitions and copy the files over to the new partitions.

cp -r --preserve=all  /source  /destination

Then you have to install grub to the new drive. There are several ways to do that, too, and lots of descriptions on this board. 

It's also possible to copy the files with rsync, and that might be the better way, but it's not easy if you don't already know that command. If you do it with dd, you'll end up with partitions the same size as your source.

---

