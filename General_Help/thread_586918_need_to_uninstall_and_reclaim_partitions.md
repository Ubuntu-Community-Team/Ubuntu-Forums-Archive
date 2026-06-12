---
title: "need to uninstall and reclaim partitions?"
date: 2007-10-22
forum: General Help
---

### Post by intellijel on 2007-10-22
I installed Ubuntu 7.04 on a 500Gb HD with XP Pro already running. I have also have a second 500Gb HD

When I first tried to install ubunut and it was creating a partition, it hung for a long time not doing anything (30 minutes). I exited the installer and it looks like I may have interrupted the install process.

I re-installed ubunut and this time I let it run it's course and it installed fine. I chose for ubunut to make an 80gb partition on my main HD so that the remaining space was left for XP.

Now when I boot windows I see that I only have 50.9GB of HD space on each of my 500GB HD and the rest has been allocated to ubuntu!

How do I fix this??

Do I need to backup my windows data and then re-format both drives and then reinstall WIndows?

Can I resize the partitions and merge the extra space with the exisiting windows partitions?

The ideal situation would be to have a single 80GB parition on the primary drive for ubunut with the rest of the drive as a single partition for windows. The second drive should only be for windows (NTFS)

Any help would be greatly appreciated!!

---

### Post by mikewhatever on 2007-10-22
Use the installation CD and System>Admin>Gnome Partition Manager. It is important to do it from the CD and not from your Ubuntu installation, because in the first case no partition is mounted, and thus, can be modified.

Edit: I've checked Ubuntu 7.10x64 desktop CD, and the Partition Manager is not there. Either use the 7.04 or download Gparted live cd.

---

### Post by intellijel on 2007-10-22
hey thanks for the reply

So I have a 7.04 install disk, I just boot into that and choose the option "run or install" ubuntu?

Will I get the chance to run the partition utility at that point?

thanks!

Danjel

---

### Post by intellijel on 2007-10-22
I have answered some of my own questions already:

CD boots into ubuntu, I open gnome partition manager. I was able to delete the partition on the second drive and then resize the NTFS partition to max.

On the first drive I have been able to re-size ext3 to 20gb.... is there a way to make the remaining unallocated space part of the NTFS partition that windows xp is on? (the other drive was just a data drive)


thanks!

---

### Post by intellijel on 2007-10-22
ok that is not working out since the second drive is being used for swap memory (I don't want ubuntu to be using that drive at all). I can re-size it and leave the 10gb it is using...but I would rather erase al traces of ubuntu on that drive.

---

### Post by mikewhatever on 2007-10-22
Try checking the documentation [http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php).
I am not sure if it can handle ntfs formatting, since that's MS only file system.

---

