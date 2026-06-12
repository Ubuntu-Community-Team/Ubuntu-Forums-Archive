---
title: "Deny acces to partition (Partition permission)"
date: 2007-08-11
forum: General Help
---

### Post by shironeko on 2007-08-11
I got windows partition, which does automount when I start the computer.
Now what I would like to do is to restrict the access, of a certain user, to this partition.

I don't want him to enter it.

I've tried with Chmod, but no luck.

Thankyou.

---

### Post by bettlebrox on 2007-08-11
You can change the mount options so that the filesystem is mounted by your UID & GID.

FAT32 filesystems don't support Linux permissions, so you need to set the ownership at mount time (the default is root).

This page should help:

[http://gentoo-wiki.com/HOWTO_Mount_Windows_partitions_(DOS,_FAT,_NTFS)#uid.2Cgid:_mount_as_.28user.2Cgroup.29](http://gentoo-wiki.com/HOWTO_Mount_Windows_partitions_(DOS,_FAT,_NTFS)#uid.2Cgid:_mount_as_.28user.2Cgroup.29)

---

