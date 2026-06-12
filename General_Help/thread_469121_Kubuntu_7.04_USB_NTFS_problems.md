---
title: "Kubuntu 7.04 USB NTFS problems"
date: 2007-06-09
forum: General Help
---

### Post by pestilence on 2007-06-09
I have posted this into the Kubuntu forums as well.
I recently installed Kubuntu 7.04 on my laptop and I experiencing problems with KDE and HAL, I have 2 external disks, 1 WD with VFAT filesystem and 1 MAXTOR with NTFS (2 partitions).
When I plug my WD disk (USB) which is VFAT everything works ok, the disk is auto-mounted under KDE and I can access it as normal.
Problems start when I plug my MAXTOR NTFS USB drive. The drive is recognized correctly under KDE, but when I try to mount it I get problems. To be more precise here is the procedure with screenshots:
[[IMG]http://img257.imageshack.us/img257/5079/snapshot1eg0.th.png[/img]](http://img257.imageshack.us/my.php?image=snapshot1eg0.png)
[[IMG]http://img257.imageshack.us/img257/6761/snapshot2fg7.th.png[/img]](http://img257.imageshack.us/my.php?image=snapshot2fg7.png)
[[IMG]http://img248.imageshack.us/img248/58/snapshot3cs6.th.png[/img]](http://img248.imageshack.us/my.php?image=snapshot3cs6.png)

As you can see when I plug my external drive it is recognized, but furthermore I am unable to mount.
Removing the "mount as user flag" allows me to mount it, but due to root privilleges I am unable to browse the files through konqueror (as a normal user):
[[IMG]http://img176.imageshack.us/img176/1082/snapshot4qn9.th.png[/img]](http://img176.imageshack.us/my.php?image=snapshot4qn9.png)
[[IMG]http://img176.imageshack.us/img176/1286/snapshot5br3.th.png[/img]](http://img176.imageshack.us/my.php?image=snapshot5br3.png)
[[IMG]http://img254.imageshack.us/img254/1883/snapshot6hg4.th.png[/img]](http://img254.imageshack.us/my.php?image=snapshot6hg4.png)

P.S My Kubuntu 7.04 installation is up to date.
P.S2 This is only happening to NTFS formated filesystems, FAT32 sticks etc are able to get mounted properly.
Furthermore:
[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/110210](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/110210)

---

### Post by olujicz on 2008-02-09
I have the same problem, and this was my solution.

Once the external hard drive has been found right click and open up its properties. And then uncheck the mount as user box.

---

