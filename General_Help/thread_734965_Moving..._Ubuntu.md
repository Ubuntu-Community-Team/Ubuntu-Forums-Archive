---
title: "Moving... Ubuntu?"
date: 2008-03-25
forum: General Help
---

### Post by AbsentHarvest on 2008-03-25
My windows partition is growing a demand for more hard drive space.  I only sometimes use Ubuntu.  So I'd like to set some priorities.  I have an External Hard Drive, a 320GB one.  It acts as a regular hard drive, only not in the computer. :P Which I can find in the Partition Editor in Ubuntu.  Located on the top right drop menu.

My real question, is i'd like to move Ubuntu 7.10 to my external.  Also the GRUB bootup.  Because if for some reason i'm away from my external, the computer will fail to start because GRUB will want to find Ubuntu.  So if possible i'd like to move that.  Is this possible?

I've read this post.
[http://ubuntuforums.org/showthread.php?t=268434](http://ubuntuforums.org/showthread.php?t=268434)
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

Only it doesn't mention anything about GRUB.
Or removing the old disk image.

---

### Post by cdenley on 2008-03-25
I would boot to a livecd, partition/format your external drive, copy your files, edit /boot/grub/device.map on your external drive, then run
```

sudo grub-install --root-directory=/media/disk /dev/sdb

```
Where /dev/sdb is your external drive, and your new ext3 partition is mounted at /media/disk.

---

