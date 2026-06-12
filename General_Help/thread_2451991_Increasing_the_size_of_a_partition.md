---
title: "Increasing the size of a partition"
date: 2020-10-14
forum: General Help
---

### Post by hebs01 on 2020-10-14
I just started using Ubuntu, i was meaning to duel boot windows but gave up. Now i want to increase the size of my Ubuntu partition by giving the 201 gb of free space to it but when i click on resize it does not give me the option. I have also tried using KDE and gparted but neither seem to work. Would really appreciate it if someone was able to help[ATTACH=CONFIG]287153[/ATTACH]

---

### Post by tea for one on 2020-10-14
You can only resize partitions that are not in use i.e. **unmounted**.

Use your Ubuntu usb device and boot into a [COLOR="#0000FF"]live[/COLOR] session.

Gparted is already installed in the original Ubuntu iso (when using a live session).

Make sure that you have backups of your data because using a partition manager can be destructive if not careful.

---

### Post by oldfred on 2020-10-14
Are you running gparted from Ubuntu live installer? Little key icon will say partition is locked/mounted.
All partitions have to be unmounted, or you cannot run from your installed system.
I do use gparted on my installed system, but only for other drives with all partitions unmounted.

I prefer smaller / (root) partitions and either larger /home or what I use data partition(s).
If newer user, easier to use separate /home as that creates mount point, and gives you ownership & permissions. If using data partition you have to do all that yourself.

To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) & 
[https://ubuntuforums.org/showthread.php?t=2343317](https://ubuntuforums.org/showthread.php?t=2343317)

[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by hebs01 on 2020-10-14
never mind, thank you for your help, i just misunderstood and can't find how to delete thee question now

---

### Post by hebs01 on 2020-10-14
ok, thank you so much

---

