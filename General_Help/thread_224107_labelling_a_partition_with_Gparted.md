---
title: "labelling a partition with Gparted"
date: 2006-07-27
forum: General Help
---

### Post by jordilin on 2006-07-27
Is there a way to label a partition with GParted. It formats and partitions my external hard drive but I have no option to put a label on it.

---

### Post by x64Jimbo on 2006-07-27
I noticed this problem as well. I know that QtParted works for labeling partitions, so you might try that instead.

---

### Post by wpshooter on 2006-07-27
> **jordilin said:**
> Is there a way to label a partition with GParted. It formats and partitions my external hard drive but I have no option to put a label on it.

My **guess** is that this is because it already has a label.

If I wipe one of my hard drives using a hard drive wiping utility before I use gparted to set up the partitions, it always ask me to either verify the default label that gparted assigns or to give a new label name.

I am **assuming** this would function the same way on an external drive.

Good luck.

---

### Post by jordilin on 2006-07-27
Solved!!. If you want to put a volume label to a formatted external hard drive, you can by issuing:
```
e2label /dev/sdaX nameofthelabel
```
With this, everytime you plug in your hard drive, flash drive, or anything, Ubuntu mounts it automatically and a folder with the name of nameofthelabel appears in your desktop. Cool, isn't it!! :cool: 
Thanks everyone.
PD. sdaX where X is the number where your harddrive sits. Doing a ```
df -k 
``` tells you this.

---

