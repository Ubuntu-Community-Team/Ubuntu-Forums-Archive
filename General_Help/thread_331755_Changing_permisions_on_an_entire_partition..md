---
title: "Changing permisions on an entire partition."
date: 2007-01-05
forum: General Help
---

### Post by tehhaxorr on 2007-01-05
I need to find out how to change the permissions for the entire partition /dev/sda5 (All files and folders) so my user "mark" has complete read & write access. /dev/sda5 has all of my multimedia on it, it is a fat32 drive that is also the D: drive in windows. i have sda5 mounted at the moment to /home/mark/Multimedia, but i'm sick of running my media programs as root just to edit the files. ](*,) 

Help!

---

### Post by yabbadabbadont on 2007-01-05
[Doc link]("http://gentoo-wiki.com/HOWTO_Mount_Windows_partitions_%28DOS%2C_FAT%2C_NTFS%29#uid.2Cgid:_mount_as_.28user.2Cgroup.29")

That is from the Gentoo wiki, but the options described will work when added to the /etc/fstab on any linux distribution.

---

