---
title: "iPod mount options and mstab question"
date: 2007-05-22
forum: General Help
---

### Post by bobabot1 on 2007-05-22
When I first plugged in my ipod mini, it automatically mounted itself and all was good. When I tried getting gtkpod to recognize it so I could manage my music, it said that I needed to change the mount point to /media/ipod. I went and edited the mount point but accidentally used "/" and made it unmountable. I went backed and fixed that but now it says I am now using invalid mount options. 

I would like to know what are the correct or default mount options for an ipod.

My current (not working) options: "rw umask=077 gid=1000 uid=1000 user defaults noatime iocharset=utf8 0 0"

Also, I have my hard disk partitioned with two fat partitions that I want mounted on each boot-up. They only mount after I open Gnome partition editor. I have heard that fstab is used for "permanent" drives and mstab is used for "removable" drives. My FAT partitions only show up on mstab and I'm wondering if that is the problem.

---

### Post by mitch.c on 2007-05-23
> **bobabot1 said:**
> I would like to know what are the correct or default mount options for an ipod.

My current (not working) options: "rw umask=077 gid=1000 uid=1000 user defaults noatime iocharset=utf8 0 0"
Are you saying that this is what's listed in /etc/fstab (if so, options need to be comma separated), or are you trying to mount you iPod manually? Will you please clarify?

I have absolutely no entry in fstab for my iPod Nano and it automatically mounts when connected using both KDE and Gnome.

> **bobabot1 said:**
> Also, I have my hard disk partitioned with two fat partitions that I want mounted on each boot-up. They only mount after I open Gnome partition editor. I have heard that fstab is used for "permanent" drives and mstab is used for "removable" drives. My FAT partitions only show up on mstab and I'm wondering if that is the problem.
I'm not familiar with mstab, are you referring to /etc/mtab? If so, this file is dynamic and lists currently mounted file systems. You are correct about /etc/fstab, you need to make an entry for each FAT partition you want mounted at boot. For example,
```
# mounts /dev/sda3
/dev/sda3       /home/shared   vfat    defaults,utf8,umask=007,gid=46 0       1
```
You may want/need a different umask and gid value.

---

