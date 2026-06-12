---
title: "add a partition"
date: 2016-12-19
forum: General Help
---

### Post by zandu on 2016-12-19
Hi what is the easiest way to add an extra partition to 14.04 so that I can use it for extra data.

---

### Post by howefield on 2016-12-19
> **zandu said:**
> Hi what is the easiest way to add an extra partition to 14.04 so that I can use it for extra data.

Shrink an existing one and create a new partition with gparted or add a new disk to the fstab file. Probably.

Would be good to know your existing partition layout, can you post an image taken with gparted or post the output of 

```
sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
```

---

### Post by Impavidus on 2016-12-19
First create the new partition. Should be easy if it's on a new hard drive. You can use gparted (not installed by default, but available by default in a live session). If you have to modify existing partitions, you may have to do it from a live session. Don't use Linux tools to modify Windows partition. They may work, but not always. Use Windows tools instead and reboot Windows a couple of times.

When your new partition is ready, use fstab to mount it automatically at boot. Create directories and set permissions as you please and it's ready for use.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

