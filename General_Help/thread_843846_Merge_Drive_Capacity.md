---
title: "Merge Drive Capacity"
date: 2008-06-28
forum: General Help
---

### Post by masterdam79 on 2008-06-28
Hiya all,

I've just installed Ubuntu 8 and loving it.
I've also sticked in my two 320GB IDE drives and formatted them EXT2 (EXT3 didn't show up for some reason)
Now I heard that Ubuntu can merge the capacity of those two drives into one massive 640GB drive.
I've tried mounting the two drives to the same folder;

root@ubuntu7:~# mount /dev/sdb1 /media/JOINED
root@ubuntu7:~# mount /dev/sdc1 /media/JOINED

But then it shows only one of the two drives in that folder.

Anyone tried this?:popcorn:

---

### Post by sdennie on 2008-06-28
You'd have to setup LVM or RAID to do this.  I've only looked at this guide briefly but, it seems to explain all the steps: [http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem](http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem)

Alternatively, you can probably copy all the data to one drive, set the other to use LVM, copy the data back to the LVM drive, make the other drive LVM and then add it to the first LVM drive group(s).  You can probably find a guide for doing that.

---

### Post by HalPomeranz on 2008-06-28
It's usually not a good idea to concatenate two drives together unless you're also mirroring them.  The problem is that if one drive in the concatenated file system fails, you lose the data on both drives because the whole file system is corrupted.

So frankly you're better off continuing to use them as separate drives.  If one fails, at least you'll still be able to get data off the other one.

---

### Post by Virtualburn on 2009-11-05
I have the opposite issue of Ubuntu 9.10 picking up my 2 250GB drives as one when I run this installation.. how can I prevent this?  They are not using RAID and within wndows are separate.

DELL Dimension 9150.

---

