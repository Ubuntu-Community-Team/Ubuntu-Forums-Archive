---
title: "re-mounting SATA disk"
date: 2008-01-30
forum: General Help
---

### Post by Green_Star on 2008-01-30
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84603](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84603)

I have serious problem with this bug, any way this disk is secondary disk, so my OS dont freeze when disk is freeze. It works fine when I reboot the computer. 

when I try to umount command to disconnect disk, it is saying disk is busy. so i am rebooting.

But it is very annoying to reboot many times a day. Is there any way to re-mount this disk without rebooting?

---

### Post by Green_Star on 2008-02-08
any one?

---

### Post by Rocket2DMn on 2008-02-08
You can try forcing it to unmount:
```
sudo umount -f /path/to/mount/point
```
Or using
```
sudo umount -l /path/to/mount/point
```
That's a lowercase L, and it should unmount the drive after it's not busy anymore (sounds weird but it's been known to work sometimes).

---

