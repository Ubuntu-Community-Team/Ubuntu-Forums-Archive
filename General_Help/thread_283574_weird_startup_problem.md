---
title: "weird startup problem"
date: 2006-10-24
forum: General Help
---

### Post by heartsmagic on 2006-10-24
I installed Ubuntu 6.06 one of my friend's computer. This computer has 2 hard disks, on the first one there is Windows, so i installed linux on 2nd hdd. Everything seems alright, i booted Linux several times, there was no problem. But after i went home, they booted to windows and after that tried to boot Linux again and got that error:

Loading, please wait...
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /dev on /root/dev failed: No such file or directory
Target filesystem doesn't have /sbin/init

I saw some similar problems on the forum, but they are about fstab or partitions. But our fstab is normal and also partitions. i solved that problem by doing fsck to this hdd. Ubuntu booted again, but after booting to windows, the error appeared again. I couldn't find why this is so. I wonder if there is somoone who encountered similar problem before.

---

