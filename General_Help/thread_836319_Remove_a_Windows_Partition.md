---
title: "Remove a Windows Partition"
date: 2008-06-21
forum: General Help
---

### Post by dlbrando on 2008-06-21
Running 8.04 on a desktop that has a 40gb HD.  linux is partitioned into a 13gb box that it has filled.  I did not know that it was partitioned like that, must have overlooked it.  the partition editor will not touch it, neither will fdisk?  How do I remove the partition and all of its contents.  The system will not let me delete the contents either.  It is only a windows setup that I no longer need, I just want it to go away so I can use the whole hd.

---

### Post by forestpixie on 2008-06-21
Remove the windows or linux partition? Regardless of which there is a partition editor on the livecd you installed from if you're using hardy - can't remember if gutsy or feisty has one. 

OR get partedmagic or gparted and burn it as an iso so yopu can boot with it.

You will not be able to work with the partition while it's mounted.

If you are deleting the linux partition make sure you fix the mbr before you remove linux or it won't find grub.

If you are deleting the win you won't have that problem.

Bott a livecd - delete the offending partition and resize the other.

---

