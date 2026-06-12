---
title: "How to repair linux filesystem? Error during start-up."
date: 2007-11-30
forum: General Help
---

### Post by revi_2003 on 2007-11-30
Hello all,

I have run into some problems starting up Ubuntu 7.10.

My Ubuntu installation is not booting up. I get the following error under recovery mode:

Begin: Running /scripts/local-bottom...
Done.
Done.
.: 195: Can't open /etc/default/rcS
error: '/etc/init.d/rc' exited outside the expected code flow.
init: rcS main process (2452) terminated with status 2
root@(none):~#

I was told to try a fsck through a live CD. I tried and it does not work.

Thanks in advance

---

### Post by bingoUV on 2007-11-30
When you say fsck through a live CD does not work, what does it mean? Is there some error? Can you find the appropriate partition in the live CD session?

---

### Post by revi_2003 on 2007-11-30
> **bingoUV said:**
> When you say fsck through a live CD does not work, what does it mean? Is there some error? Can you find the appropriate partition in the live CD session?

bingoUV,

I type:
fsck /media/disk

and get the following error:

fsck.ext2: Is a directory while trying to open /media/disk

The superblock could not be read or does not describe a correct ext2 filesystem.

My filesystem is ext3 type. Is that a problem?

Thanks

---

### Post by bingoUV on 2007-12-01
give the device name rather than the directory name. See the output of 
```

sudo /sbin/fdisk -l

```

This will print out all your hard disk partitions. Recognize the partition that you are interested in (by size, filesystem type etc.). Suppose it is /dev/sda1.  Now unmount it, so that it is safe to fsck it; and then run fsck
```

sudo umount /dev/sda1
sudo fsck /dev/sda1

```

---

