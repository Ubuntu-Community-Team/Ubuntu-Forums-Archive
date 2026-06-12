---
title: "Permissions for a Mounted Partition"
date: 2008-01-09
forum: General Help
---

### Post by ThorX89 on 2008-01-09
Hi. I am trying to mount some NTFS partitions with some specific access rights, but so far I've been only able to mount them accessible to either anyone or root only.

E.g. I wanna mount /dev/sdb9 to /media/mda with permissions 774 and I guess this line in fstab should do so:
> /dev/sdb9 	/media/mda      ntfs    defaults,user,uid=1000,gid=100,umask=744  0       0
However, it does not, and when I try to open the folder in nautilus it is inaccessible, as the octal permissions are inexplicably 033. (both the group and owner have been assigned correctly, though)

Anyone know how to solve this?

---

### Post by capink on 2008-01-09
> **ThorX89 said:**
> Hi. I am trying to mount some NTFS partitions with some specific access rights, but so far I've been only able to mount them accessible to either anyone or root only.

E.g. I wanna mount /dev/sdb9 to /media/mda with permissions 774 and I guess this line in fstab should do so:

However, it does not, and when I try to open the folder in nautilus it is inaccessible, as the octal permissions are inexplicably 033. (both the group and owner have been assigned correctly, though)

Anyone know how to solve this?

umask is the opposite of permissions. so you should make it umask=033 to work

---

### Post by geirha on 2008-01-09
umask is sort of the reverse of the permissions you want, i.e. you set the permissions that shouldn't be set. Try with umask=022,fmask=133 which should give all dirs 755, and all files 644

EDIT: And if you want to be able to write to the filesystem, you'll need to use ntfs-3g as filesystem type instead of ntfs

---

### Post by ThorX89 on 2008-01-09
THX a lot. :-D 033 = 777 - 744 in octal, of course. :-)   It should've occured to me!

---

