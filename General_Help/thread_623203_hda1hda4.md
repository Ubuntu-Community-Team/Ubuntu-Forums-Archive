---
title: "hda1/hda4"
date: 2007-11-25
forum: General Help
---

### Post by Swiss Made on 2007-11-25
Alrighty, so I followed some tutorial on how to dual boot Windows XP/Ubuntu 7.10.

hda1 = Windows XP
hda2 = 5gb ext3 (Ubuntu/Software)
hda3 = 1gb swap
hda4 = 50GB or so (files/storage)

Now everything works fine, I can dual boot to windows or ubuntu without any problems, my problem is, hda4

Another weird thing is, hda1 is showing up on my HD, and I can view all my windows xp files as if it were C:.

Now back to my real issue, hda4, when I open it has a folder within called "lost+found" with an x in the top right corner of the folder icon, when i try and open it, it says "The folder could not be displayed, you do not have the permission necessary to view the contents of "lost+found".

All I want is for hda4 to be able to save files into, such as music/videos/whatever else,

I used GParted to set up the partitions, do I need to delete hda4 via GParted and reformat it somehow?

Sorry if this seems like an easy question, but I am pretty new to linux.

- Swiss Made

---

### Post by ray bot on 2007-11-25
When you create an ext3 partition, it automatically gets a folder called "lost+found".  This is where fsck will put corrupted or orphaned files if you ever get any errors with that partition.  The reason for the error message you got is that the folder is owned by root.  This is nothing to worry about; you can just ignore that folder, unless you've had problems with your partition.

---

### Post by kaiju on 2007-11-25
i am assuming that you formatted hda4 as ext3. if that is so, then you have the lost+found folder (marked as accessible only for root with the little x) because fsck (the program that checks ext filesystems for integrity every once in a while) needs it so it can place recovered files into it (eg. after a system crash).

now to the real thing:
you open a terminal (gnome-terminal) and go to your hda4 disk
```
cd /media/hda4
``` (or whatever the mountpoint is)
then do a
```
gksu nautilus
```
and under properties then permissions, change the read/write permissions. my disks have:

owner: root (create and delete)
group: plugdev (create and delete)
others: (none)

or you can just change the owner to your user and give it read and write permission.

---

### Post by kaiju on 2007-11-25
ray bot, you were faster than me.
respect :)

---

### Post by Swiss Made on 2007-11-25
Thanks for your help guys, I thought for some reason I did something wrong, but I guess that's normal then.

:guitar:

---

