---
title: "External HDD - Permissions"
date: 2007-01-26
forum: General Help
---

### Post by qalimas on 2007-01-26
Recently, I've gotten complaints about a computer I loaded Kubuntu on.  I go and see about it, and it boiled down to the external hard drive (USB) not allowing permission changes.  The hard drive is formatted as FAT32 (Windows needs access through VMWare).

When I run the chmod command, for example: "chmod 777 /media/SEAGATE/transfer/file1.jpg", the command runs, but the change does NOT take place.  The file still stays 700.  The user I'm chmodding as is seen as the owner, and even putting sudo in front of it will not let the changes take place.

Am I correct in assuming it is because the partition is FAT32?

If so, will ext2 allow me to fix this (I heard there is a plugin for Windows for ext2 access)?

Thanks for any help =)

---

### Post by taurus on 2007-01-26
Chmod won't work with ntfs & fat32 filesystems.  You need to mount it with the right permissions though.

```
sudo umount /media/SEAGATE
sudo mount -t vfat /dev/sda1 /media/SEAGATE -o iocharset=utf8,umask=000
```
Or convert it to ext3 and use fs-driver, [http://www.fs-driver.org](http://www.fs-driver.org), to read and write to ext3 from Windows.  Then, you can use chmod command.

---

### Post by qalimas on 2007-01-26
Would there possibly be a way to convert it to ext2 without having to back everything up, reformatting, and moving it back?

---

### Post by taurus on 2007-01-26
When you format it from vfat to ext3, you will loose everything so you have to back the files up first.  Otherwise, try to see if your user can write to it with those two commands that I included above.

---

### Post by qalimas on 2007-01-26
I will, when I have access to the computer (in about another 2-3 hours).  It's not at my home.

Assuming that does work, what would I add (or change) in fstab to make it auto-mount with those properties?  If need be, I'll post the fstab in a few hours when I get the chance.

(I'm sorry for asking so much, I've never really dealt with Windows partitions in Linux.  I'd be fine if the stupid thing was ext3 and Windows didn't need access... but she needs Photoshop. =/)

---

### Post by taurus on 2007-01-26
```
/dev/sda1   /media/SEAGATE   vfat   iocharset=utf8,umask=000   0   0
```
Don't forget the [http://www.fs-driver.org](http://www.fs-driver.org) if you want to convert that harddrive to ext2/ext3 so she can access it from Windows.  ;)

---

