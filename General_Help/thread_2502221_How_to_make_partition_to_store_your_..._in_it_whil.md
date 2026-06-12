---
title: "How to make partition to store your ... in it while you have /home partition?"
date: 2024-11-05
forum: General Help
---

### Post by 123nbom on 2024-11-05
Hello guys.

I have two partitions to store my data on them, but in linux you only allowed to make a home partition only one. But how can i format the other partition because i need it i need to store data on it. Like in windows you can make many partitions as you like EXample E: G: I: and C: for windows only.

---

### Post by Bashing-om on 2024-11-05
123nbom;

It is trivial to make up a data partition in Linux - once you know how.
That know how takes a learning curve advancement :)

For a desktop user I would highly suggest the utility 'gparted' to set up the new partition.
In order to properly guide you we need some basic drive info.
Please post back the result of terminal command - between code tags -:
```

sudo fdisk -lu

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
As the 1st thing we need to know; where we see what the partitioning and type are.

[INDENT]longest journey starts with the 1st step
[/INDENT]

---

### Post by grahammechanical on 2024-11-05
> Like in windows you can make many partitions as you like EXample E: G: I: and C: for windows only.                 

How do you explain that I have 5 partitions on my drive? I have 3 installs of Ubuntu each without a separate Home partition but I could have given each its own Home partition. Instead I have a partition set aside for Data that I can access from each install of Ubuntu.

> I have two partitions to store my data on them,

Are these Windows partitions? Please show us the layout of the partitions of your drive. Any partition formatted as Ext4 can be accessed by any install of Ubuntu. Open the file manager. Click on Other Locations and there you will see the other partitions on the drive. They will be called volumes. Click on one and you will see the folders on that partition.

Once the file manager has clicked on a volume it is "mounted" as they say in Linux. Now applications can browse to the partition and save documents in folders in that partition. Or, open files in folders on the partition. The application will even remember where the document came from and save to that location or retrieve the document from there. For this to work the partition has to be mounted and the file manager can do that.

It is also possible to set up Ubuntu in such a way as the auto-mount these other partitions the same as it auto-mounts a Home partition.

Regards

P.S. Using to create/delete folders on these other Ext4 partitions is another skill to be learnt.

---

### Post by TheFu on 2024-11-05
> **123nbom said:**
> Hello guys.

I have two partitions to store my data on them, but in linux you only allowed to make a home partition only one. But how can i format the other partition because i need it i need to store data on it. Like in windows you can make many partitions as you like EXample E: G: I: and C: for windows only.

I think you are confused.  You can connect thousands of HDDs with tens of thousands of partitions/file systems to almost any Linux computer.

Also, you can have as many HOME partitions as there are users on Linux.  Ubuntu with Snaps will have some issues, but if you remove all snaps, then that issue is also removed.  Any distro that doesn't mandate snap packages never had this issue.

I suspect you just don't understand how to mount storage where you need it or how to use symbolic links.  [https://en.wikipedia.org/wiki/Symbolic_link](https://en.wikipedia.org/wiki/Symbolic_link) will explain a bit.  The command to create a symlink is **ln -s** - there are a few other arguments necessary and different forms, so don't just blindly type that in.

With MS-Windows, what happens when you run out of drive letters?  BTW, those aren't really "drives" - they are file systems, but MS has been dumbing things down incorrectly for many decades.  Linux admins are expected to be smarter.  Anyway, drive letters ARE limited in MS-Windows from A-Z, so 26 are allowed, but they finally started allowing mounts into specific locations around 2005, so don't worry.  Unix/Linux systems allow placing mounts on any directory - but it is best if it is an empty directory and not under any user's HOME for a number of reasons.  Some unexpected things can happen to the admin who doesn't address the likely issues caused by mounting extra storage under a user's HOME directory somewhere.

---

### Post by oldfred on 2024-11-05
Several more threads with separate data partition(s) and linking.
[https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909](https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909)  & 
[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198) &
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

Back with XP, I would have a shared NTFS data partition and a Linux data partition as standard mounts in fstab plus many other partitions as temporary mounts.

For new uses the separate /home is relatively easy. It formats, mounts, provides default ownership & permissions & has default folders.
But for data partitions, you have to create partition, format partition, mount partition (either manually or in fstab) and give yourself ownership & permissions. You also then have to create whatever folders you want. Not difficult but more steps.

---

