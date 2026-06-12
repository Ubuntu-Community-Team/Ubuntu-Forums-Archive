---
title: "crash gparted... all data lost!"
date: 2007-04-26
forum: General Help
---

### Post by trampolando on 2007-04-26
Hello, I was using Gparted for enlarging a ext3 partition, using some unallocated space that i have on the left of that partition.
Gparted  was moving all the files.... while my computer crushed, I think for a hardware cause.
After rebooting my pc the partition was impossible to mount, I've tried fsck, e2fsck, and many other tools, like photorec, but unsucessfully.
How can i recover my data inside the partition?
The final result after the operation of gparted expected to be  a hard-disk with only two partitions, but now the incriminated partition isn't big as much as I expeted, and there is 40 Gb of unallocated space at the end of the hard-disk. I think my data are still there.
Using Photorec I've managed to find some photos, but not the one i was searching for....
Photorec ask me some parameter that I don't know, such as block size, and offset.
Can anyone suggest me something, or a commercial software to use that can recover my data?
thanks a lot

Does anybody know what gparted is doing enlarging a ext3 partition that contains data, using unallocated space on the left?

---

### Post by frodon on 2007-04-26
The good news is that all your file should still be there but for me you partition is lost because gparted surely didn't have the time to put a end flag to the partition. BTW enlarging a partition may introduce some data lost even if sucessful.
Anyway there's other tools to allw you to recover some data but be careful it can be a long process. I would advice you "ddrescue" first since your drive is not corrupted or dead you may have good result with it but as i said you the data recover will spend a couples of hours (last time i used it it took 4-5 hours).

Here is a nice guide which will explain you how to use ddrescue and recover your datas :
[http://www.titov.net/2005/12/31/how-to-restore-reiserfs-partition-from-crashed-disk/](http://www.titov.net/2005/12/31/how-to-restore-reiserfs-partition-from-crashed-disk/)

---

### Post by trampolando on 2007-04-29
Nucleus kernel linux, a proprietary software, solved all my problems: it recovered almost all of my data.

---

