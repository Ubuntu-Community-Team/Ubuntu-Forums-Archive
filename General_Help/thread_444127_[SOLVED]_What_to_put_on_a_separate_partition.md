---
title: "[SOLVED] What to put on a separate partition"
date: 2007-05-15
forum: General Help
---

### Post by Tautoa on 2007-05-15
After reading around a bit, i decided to move my /home folder to a separate partition. This turned out to be a pretty good decision the next time I messed up and had to reinstall Ubuntu :) I'm wondering, is there anything else that would be beneficial to have on its own partition? I'm dual booting with Windows, and I've already got something similar with my Documents and Settings and Program Files folders. Having used Ubuntu less than a month, I'm still not overly sure what the  various folders are, despite googling. Any ideas? :)

---

### Post by heimo on 2007-05-15
> **Tautoa said:**
> I'm wondering, is there anything else that would be beneficial to have on its own partition?

Home directory is the most important for most of us. If you ran web server (or any other kind of server) you'd probably want to put /var on its own partition too. And then it's also helpful to take backups of any system wide configuration files that you change thorugh GUI or directly using text editors. These live under /etc, but it really doesn't need its own partition.

---

### Post by hartz on 2007-05-15
Warning: putting /etc in its own partition will break things.

The system expects to be able to read configuration files after mounting the root disk, before mounting other disks.

In particular, the config file that tells the kernel where to mount what partition, resides in /etc.  The file is /etc/fstab (the "File Systems Table" file).

If /etc is made into a separate partition, the system will not be able to read the fstab file, and so will not be able to determine where to find the /etc or any other partitions.

---

### Post by Tautoa on 2007-05-17
Ok, thank you :)
What would be the Linux equivalent to Program Files in Windows, if there is one? I'm looking for a way to keep all my programs on a separate partition, I tend to mess with files that I probably shouldn't, and as a result, seem to be reinstalling the OS on a regular basis...
I know I should make backups before messing with things, but.... :rolleyes:

---

### Post by kefir on 2007-05-17
That would be /usr

---

### Post by Tautoa on 2007-05-17
Thank you! This should save me from reinstalling programs next time I mess my computer up :)

---

### Post by abuno on 2007-05-17
Have also separate partitions. 
My problem is that i  made the /usr to small. DAMNIT!
It is full and i can't install a program.
to solve it, i manage to resize a other partition.
The free space, i set it up as ext3 and /usr in the partition manager

the problem is that ubuntu doesn't recognise the partition as /usr
(it was just a guess, it would)
In stead it has the name disk-1

Or is it better to resize the original /usr partition to a bigger one
(Can this be done, or will it be harmfull?)

As you see I'm a NOOB.
So help me please

ps. I want to run Maya whit a menu item  and whit this command export MAYA_MMSET_DEFAULT_XCURSOR=1; maya

How can i make this item?

---

