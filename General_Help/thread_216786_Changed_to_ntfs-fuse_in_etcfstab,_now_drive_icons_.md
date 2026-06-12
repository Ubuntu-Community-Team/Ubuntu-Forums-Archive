---
title: "Changed to ntfs-fuse in /etc/fstab, now drive icons on desktop and places don't show"
date: 2006-07-16
forum: General Help
---

### Post by crazygamer on 2006-07-16
As the title says, I installed ntfsprogs and switche to using ntfs-fuse to get read/write support for my NTFS partitions. Before, when just using "ntfs" in fstab, I had nice icons for my NTFS partitions on my desktop and in the places menu. Now the icons for my "ntfs-fuse" partitions are gone. Does anyone know how I can get them back?

---

### Post by crazygamer on 2006-07-16
Bump. Last try, maybe someone will know what to do?

---

### Post by givré on 2006-07-16
You should use the new ntfs-3g, since it is more safe. Have a look there
[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)
Also, to have your partition on your desktop, the mount point in /etc/fstab should be /media/<something>

---

### Post by crazygamer on 2006-07-16
I already had my mount point in /media/hdb5, which is the same as what it was originally. The icon still isn't showing up though.

---

### Post by crazygamer on 2006-07-16
Another thing - after boot I tried unmounting /media/hdb5 and then did the following:

If I use ntfsmount to mount it, the icon on my desktop and in Places doesn't appear.

If I use mount to mount it, the icon does appear.

So I guess the question is, is it possible to get ntfsmount to place that icon on my desktop and in Places?

---

