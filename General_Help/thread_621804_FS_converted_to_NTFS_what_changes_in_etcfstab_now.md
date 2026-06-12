---
title: "FS converted to NTFS what changes in /etc/fstab now?"
date: 2007-11-24
forum: General Help
---

### Post by true_friend on 2007-11-24
HI folks
I have changed my FS of all windows drives to NTFS from FAT32 by this command in windows xp.
CONVERT F: /FS:NTFS
I have dual boot with Kubuntu 7.10 and Windows xp.
Now I want to make these drives writeable by linux systems also.
So what changes I have to make in /etc/fstab?
Regards

---

### Post by banewman on 2007-11-24
Where vfat is written in the file change it to ntfs. You'll have to reboot after.
sudo gedit /etc/fstab in terminal to make the changes ( in case you didn't know :))
Then install the prog   ntfs-3g    for read access to the ntfs partitions.
Because windows are the way they are, write support is not great from linux... :)

---

### Post by true_friend on 2007-11-24
I thought I can read write by default in ubuntu...is ntfs 3g not installed by default?

---

### Post by PmDematagoda on 2007-11-24
Yes it is, but since the fstab file entries which are automatically made when you install Ubuntu are not changed when you do any changes to your partition or drives after the installation, you will have to edit the fstab file yourself so that Ubuntu will recognise the new drive or partition and use the correct tool or system to make it accessible.

---

### Post by Route490 on 2007-11-24
Hey true_friend

An example of a fstab entry for NTFS would be

/dev/hda1 /media/Windows ntfs-3g defaults,locale=en_GB.UTF-8 0 0

Hope that helps u

Oh and if you feel like messing about with it, heres some more info [http://wiki.archlinux.org/index.php/Fstab](http://wiki.archlinux.org/index.php/Fstab)

Paul

---

