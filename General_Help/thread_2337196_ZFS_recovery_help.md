---
title: "ZFS recovery help"
date: 2016-09-15
forum: General Help
---

### Post by jaw1959 on 2016-09-15
So I just made a huge mistake. I was remoted into one machine, but thought I was connected to another machine. I thought I was deleting the partitions of a zpool on my backup machine, but I was actually deleting the partitions on my primary storage array (I was replacing the array in my my backup machine, so the array there doesn't exist...I have no backup). Is there any way for me to recover the zpool if I haven't written anything to the disks? At this point, I haven't rebooted or done anything to the drives since realizing what I'd done. I'm on Ubuntu 16.04.

---

### Post by ajgreeny on 2016-09-15
If you just deleted the partitions is is quite probable that you could recover them with [testdisk]("http://www.cgsecurity.org/wiki/TestDisk") 
Just make sure you use it on a separate system and do not use the disk with deleted partitions for anything at all.

---

### Post by jaw1959 on 2016-09-15
So you're recommending that I shut down my server, move the drives to another system, run this, and see if it can recover the lost partitions?

---

### Post by jaw1959 on 2016-09-15
This tool doesn't seem to work with zfs.  The partitions I deleted on each drive were some sort of zfs partition; and there were 2 of them.  I ran it on one drive, but it didn't seem to find anything to recover and gave some sort of message like "the drive doesn't appear to be as big as it should be." Thanks for the suggestion, but this doesn't seem like it's going to do it.

---

### Post by #&amp;thj^% on 2016-09-15
First Off I have no experience with ZFS partitions  but I was reading this yesterday and thought I would pass it along.
Looks Promising: [http://www.unixarena.com/2012/07/how-to-recover-destroyed-zfs-storage.html](http://www.unixarena.com/2012/07/how-to-recover-destroyed-zfs-storage.html)
If not best of luck.
Kind Regards

---

### Post by tl5k5 on 2016-09-15
The only way you might fix this is if you created a snapshot of the zfs.  See:  [https://wiki.ubuntu.com/Kernel/Reference/ZFS](https://wiki.ubuntu.com/Kernel/Reference/ZFS)

UPDATE:
There may be hope for you...check out this page:  [https://pthree.org/2012/12/10/zfs-administration-part-v-exporting-and-importing-zpools/](https://pthree.org/2012/12/10/zfs-administration-part-v-exporting-and-importing-zpools/)

---

