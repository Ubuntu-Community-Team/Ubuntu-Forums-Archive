---
title: "[SOLVED] Wubi file system question!"
date: 2008-07-07
forum: General Help
---

### Post by Rytron on 2008-07-07
Hi,
I installed Kubuntu in Vista using Wubi which was on the Kubuntu live cd. I was curious as to whether Wubi would change the format of the Kubuntu file to ext.
I used gparted and noticed that the file system is still in ntfs. However I have 2 hard drives on my laptop. I used 30GB of drive d which has 32GB for Kubuntu. When I used the Gparted Live Cd I saw that drive d showed up as 2GB in size. This is the amount that Vista(my other OS still has from drive D).

What file system would my Kubuntu install have? I know that it is not a dedicated partition. If it is still in ntfs, is this ok for Kubuntu?

Thanks.

---

### Post by ago on 2008-07-07
The Ubunutu filesystem is ext3 and is visible as /dev/loop0 (or loop1)
The filesystem itself is inside of the file /host/ubuntu/disks/root.disk
Where /host is the mountpoint of the containing windows device (usually ntfs).

You can use `sudo losetup -a` or `cat /proc/mounts` to gather more info.

---

### Post by Rytron on 2008-07-07
> **ago said:**
> The Ubunutu filesystem is ext3 and is visible as /dev/loop0 (or loop1)
The filesystem itself is inside of the file /host/ubuntu/disks/root.disk
Where /host is the mountpoint of the containing windows device (usually ntfs).

You can use `sudo losetup -a` or `cat /proc/mounts` to gather more info.

Thanks ago.
I also found out this way:
I went to System > KInfoCenter and discovered my Kubuntu is installed on a ext3 file system.

---

