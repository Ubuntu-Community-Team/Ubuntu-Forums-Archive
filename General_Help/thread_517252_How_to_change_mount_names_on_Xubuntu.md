---
title: "How to change mount names on Xubuntu"
date: 2007-08-04
forum: General Help
---

### Post by ZuLuuuuuu on 2007-08-04
Hi, I recently installed Xubuntu 7.04. During the installation process I choosed the mount points and it is done as I wish. However Xubuntu also placed the mount points to desktop and the names are different than the mount point names I defined. For example there is a "31G Volume" mount on my desktop which is actually mounted to "media/WinLin" I want it to be named as "WinLin" and try to change it via properties but it does not allow me, how can I change it?

---

### Post by agds on 2007-08-04
If I understand correctly, you want to change the mount point of that partition.  Here's how I would do it:

[LIST=1]
[*]Unmount the partition(s) in question.
```
umount /media/WinLin
```
[*]Make directories as needed.
```
mkdir /WinLin
```
[*]Backup and edit your /etc/fstab.
```
cp /etc/fstab /etc/fstab.bak
vi /etc/fstab
```
(Use whichever editor you prefer.  I happen to like VI.)
There should be a line that looks something like
```
/dev/hdb1       /media/WinLin        vfat    umask=000,utf8      0       0
```
I actually just ripped that line from my /etc/fstab and replaced the mount point with the one you named.  In any case, you'll want to change the path from /media/WinLin to /WinLin or whatever the name of the directory you created in step 2 is.
[*]Now save the file and remount the partition.
```
mount -a
```
[/LIST]

Naturally all the above commands must be run as superuser, i.e. via sudo if you haven't modified the default /etc/sudoers file.

---

### Post by ZuLuuuuuu on 2007-08-04
No no, thanks for your detailed reply but the mount points are all correct, just Xubuntu shows them on desktop with inunderstandable names such as: "31 G Volume", "20 GB Volume" etc... And it does not allow me to change their names. I want, for example, "20 G Volume" to be showed like "Windows XP" on desktop, otherwise the mount points are just i want them to be, in other words the problem is not about fstab. Just the names of mounted hard discs on my desktop are a little bit annoying :) Again thanks for your detailed reply...

---

### Post by taurus on 2007-08-04
I think you are talking about volume label.  You need to change it on the drive.  Do that from Windows if you wish.

---

### Post by apetresc on 2007-08-04
Hello Zuluuu :)

The name that shows up on the desktop is simply the volume name/label of the drive. This is a filesystem-related feature and not specific to Ubuntu. Fortunately Ubuntu can help you change it! Simply follow the instructions here based on which filesystem the partition is formatted as:
[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by agds on 2007-08-04
Haha, oops.  Okay, then AdrianP's suggestion looks like the way to go.

---

### Post by ZuLuuuuuu on 2007-08-04
> **taurus said:**
> I think you are talking about volume label.  You need to change it on the drive.  Do that from Windows if you wish.

It worked thanks! :)

[QUOTE=AdrianP]Hello Zuluuu

The name that shows up on the desktop is simply the volume name/label of the drive. This is a filesystem-related feature and not specific to Ubuntu. Fortunately Ubuntu can help you change it! Simply follow the instructions here based on which filesystem the partition is formatted as:
[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)[/QUOTE]

Thanks, I will use them to rename my ext3 partitions :)

---

