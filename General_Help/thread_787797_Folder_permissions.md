---
title: "Folder permissions"
date: 2008-05-09
forum: General Help
---

### Post by roccivic on 2008-05-09
I have 3 partitions on the PC, /dev/sda1 /dev/sda2 and swap
I mount /dev/sda1 in /
and /dev/sda2 in /backup

By it won't allow me to change permissions, as it is now only root can write in /backup, but I'd like to enable everyone to write there.

How do I go about this?

Many thanks for the help.

Rouslan

---

### Post by ozorba on 2008-05-09
Open a terminal window an type the followings:

sudo chmod a+rwx /backup

This will allow anyone to write to /backup partition.

Alternatively, you can change the ownership if you wish with the follwing command:

sudo chown <your login name> /backup

---

### Post by ibuclaw on 2008-05-09
What type of filesystem is your backup folder using?

If your are using a Linux filesystem (ext3/reiserfs/etc) then the above should work just fine.

Unless, if using a Windows based partition (FAT/NTFS) then you'll have to change the fstab line for the mount.

Regards
Iain

---

### Post by roccivic on 2008-05-09
> Alternatively, you can change the ownership if you wish with the following command:

sudo chown <your login name> /backup

Tried this in the terminal, it didn't return any errors, but if I right click the folder and select "Permissions" in "Properties". It still says that the folder belongs to root ans I can't change anything...

Here's a screenshot I took after I ran the command: [http://www.placella.com/Screenshot.png](http://www.placella.com/Screenshot.png)

---

### Post by roccivic on 2008-05-09
The filesystem is ext3.

---

### Post by roccivic on 2008-05-09
I rebooted and it worked.
Many thanks guys!

Rouslan

---

