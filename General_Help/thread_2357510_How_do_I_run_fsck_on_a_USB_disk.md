---
title: "How do I run fsck on a USB disk?"
date: 2017-04-03
forum: General Help
---

### Post by mringer on 2017-04-03
L-UB 14.04. One of my backup disks has developed errors. When I plug it in, 
up comes the normally-helpful message: 

```

removable medium inserted
select action
...
open in file manager

```

(that is the only action offered). Now everybody (AFAIK) agrees that you must
not run   fsck  on a mounted filesystem. So I dismount the disk, and a few 
seconds later, that message appears again. And sure enough, the disk has
re-mounted itself. 

So please: what program is doing this & how do I (temporarily) suppress this 
behaviour? Thank you.

---

### Post by yancek on 2017-04-03
Running the fsck command on a mounted partition will not do anything except produce an error message indicating the partition is mounted.

When you plug in the backup drive, do not open in the file manager but just open a terminal and type:  sudo mount
It should not show the device/partition unless you have it set to mount on boot.  If it does not show, run the fsck command.  If it does show, run umount on the partition and then run fsck.

---

### Post by mringer on 2017-04-04
> **yancek said:**
> Running the fsck command on a mounted partition will not do anything except produce an error message indicating the partition is mounted.

When you plug in the backup drive, do not open in the file manager but just open a terminal and type:  sudo mount
It should not show the device/partition unless you have it set to mount on boot.  If it does not show, run the fsck command.  If it does show, run umount on the partition and then run fsck.

But that is exactly what I was trying to do. I umounted it. Then it remounted itself.
My Q was: how to stop it remounting?

---

### Post by mringer on 2017-04-14
Bump

---

