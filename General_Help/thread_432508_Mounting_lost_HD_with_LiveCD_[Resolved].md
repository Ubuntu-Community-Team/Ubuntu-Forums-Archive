---
title: "Mounting lost HD with LiveCD [Resolved]"
date: 2007-05-04
forum: General Help
---

### Post by optimarcus_prime on 2007-05-04
I was trying to install Windows XP for a project *after* having Ubuntu for quite some time, but I was having a problem with XP so I got rid of it almost immediately after installing.  Then, when I tried to boot Ubuntu again, I get odd error messages.  On the partition containing Ubuntu, I have a backup made by following [these]("http://ubuntuforums.org/showthread.php?t=35087&highlight=howto+backup+restore") instructions [I forgot to move the backup to my external before installing XP].  I was hoping to simply access the backup and restore my system, but I can't get to it for the life of me.

This is the output of my fdisk, done using a LiveCD:
```

ubuntu@ubuntu:/$ sudo fdisk -l

Disk /dev/sda: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9169    73649961   83  Linux

```

But, when I try to mount /dev/sda1, it works, but nothing shows up in the mount point.  Any ideas?  Is it because I've got a sda drive?  I'm relatively new to this whole mount business.  Any help is appreciated!

---

### Post by aysiu on 2007-05-04
Try this:
```
sudo umount /dev/sda1
sudo mkdir /media/recovery
sudo mount -t ext3 /dev/sda1 /media/recovery
gksudo nautilus
``` Press Control-L and type ```
/media/recovery
``` and hit Enter.

---

### Post by optimarcus_prime on 2007-05-04
:-O.

You are my hero.  That was legitimately the fastest and best response I've ever got.  If this were eBay your comment would be "A+++++++++++ Excellent!"

Long story short, it worked.  Thank you so much.

---

