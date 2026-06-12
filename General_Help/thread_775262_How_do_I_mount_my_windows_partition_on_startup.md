---
title: "How do I mount my windows partition on startup"
date: 2008-04-30
forum: General Help
---

### Post by jrharvey on 2008-04-30
This may be a silly question but every prior version of ubuntu mounts my ntfs partition automatically. With Hardy, I have to mount it everytime I restart. It was a smart move to make the change but i was wondering how I can change it to mount my NTFS partition on startup.

---

### Post by ryot on 2008-04-30
You need to add an entry into /etc/fstab. Something like...
/dev/sda5    /mynewdir    ntfs   0 0

---

### Post by Ziggy72 on 2008-04-30
1. Use Gparted (or fdisk -l) to find out the name of your windows partition - let's imagine it is /dev/sda2.
2. As root, create the directory /media/sda2.
3. As root, edit /etc/fstab and enter:
```
# /dev/sda2
/dev/sda2 /media/sda2	ntfs	defaults,umask=007,gid=46 0       1
```

Obviously, if *your* windows partition is /dev/sda3, replace all the /dev/sda2's above with /dev/sda3!

Once done, you can mount the partition immediately using ```
sudo mount -a
``` The windows partition will be mounted automatically at each boot.

---

