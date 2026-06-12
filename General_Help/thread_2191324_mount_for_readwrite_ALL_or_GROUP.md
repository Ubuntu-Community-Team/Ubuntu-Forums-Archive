---
title: "mount for read/write ALL or GROUP"
date: 2013-12-02
forum: General Help
---

### Post by ridinglizard on 2013-12-02
I am trying to mount my external drive formatted ext4 to allow all in a specific group to read/write to it or I'm frustrated to the point now that I'd be happy if it allowed anyone to read/write to it.


I have
/dev/sda            /mnt/xhdd   ext4    defaults,rw,umask=0     0       3
in fstab

I've had a hard time getting it to mount at all.

---

### Post by bab1 on 2013-12-02
> **ridinglizard said:**
> I am trying to mount my external drive formatted ext4 to allow all in a specific group to read/write to it or I'm frustrated to the point now that I'd be happy if it allowed anyone to read/write to it.


I have
/dev/sda            /mnt/xhdd   ext4    defaults,rw,umask=0     0       3
in fstab

I've had a hard time getting it to mount at all.

Just a couple of things to change.  First, you should use the UUID of the partition you are mounting not the device (sda) or the partition name  (sdax).  Second,  you don't need to use umask, but if you do then you need the proper format (umask=002 (no spaces).   This is the default so it is just an example for you.  You get 775 for directories and 664 for files.

You can find the UUID of the partition from the terminal with this```
sudo blkid -c /dev/null -o list
```

So the mount in fstab will be UUID=<BLKID number listing> /mnt/hdd ext4 defaults 0  3

Note that the default options are: rw, suid, dev, exec, auto, nouser, and async.

---

