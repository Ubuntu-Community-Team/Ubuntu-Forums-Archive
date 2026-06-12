---
title: "Stop fscking me!"
date: 2007-06-03
forum: General Help
---

### Post by Nameless One on 2007-06-03
Simple question:
How do I stop fsck from checking my FAT32 partition every time I boot up? The partition is rather full and checking it each time I boot consumes a lot of time.
Thanks.

---

### Post by yabbadabbadont on 2007-06-03
Use either sudo (command line -- terminal) or gksudo (graphical) to run the editor of your choice.  Edit /etc/fstab.  Find the line that lists your fat32 (vfat) partition.  Change the '1' (could also be a '2') at the end of the line to a zero '0'.  Save your changes.  Now it will never be automatically checked.  (Just check it in windows now and then)

---

### Post by Nameless One on 2007-06-03
Great, thanks for the quick reply.
Hopefully that should sort out things. :)
EDIT: It worked :D

---

### Post by mlind on 2007-06-03
any ideas why fsck is considering your fat32 partition dirty in each reboot?

---

### Post by yabbadabbadont on 2007-06-03
> **mlind said:**
> any ideas why fsck is considering your fat32 partition dirty in each reboot?

I doubt that it is dirty.  It is just that a file system check on fat32 when the partition is nearly full takes a long time.

---

### Post by Nameless One on 2007-06-03
It isn't dirty, its just that at the 'Checking file systems' stage of boot up, every partition on my computer is checked.

---

### Post by hellmet on 2007-06-05
how do i check my filesystem then?
Manually?

---

### Post by akudewan on 2007-06-05
> **hellmet said:**
> how do i check my filesystem then?
Manually?

From the commandline, you have to unmount the partition first, and then run fsck.

Example:
```

sudo umount /dev/hda2
sudo fsck /dev/hda2

```

---

