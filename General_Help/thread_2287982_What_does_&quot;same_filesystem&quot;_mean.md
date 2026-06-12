---
title: "What does &quot;same filesystem&quot; mean?"
date: 2015-07-23
forum: General Help
---

### Post by vasa1 on 2015-07-23
I'm trying to understand hard links (in the context of rsync).

I came across [this]("http://askubuntu.com/questions/108771/what-is-the-difference-between-a-hard-link-and-a-symbolic-link"):
> ... You can only have hardlinks within the same filesystem. ...
But I'm using **rsync** with **--link-dest** to backup data (incrementally) from my laptop's hard drive to an external USB drive. [It seems to be working]("http://ubuntuforums.org/showthread.php?t=2287961"). But aren't two different file systems involved?

```
09:47 PM ~ $ df
Filesystem     1K-blocks      Used Available Use% Mounted on
/dev/sda6      219476804  14552800 193752116   7% /
none                   4         0         4   0% /sys/fs/cgroup
udev             1994280         4   1994276   1% /dev
tmpfs             401016      1232    399784   1% /run
none                5120         0      5120   0% /run/lock
none             2005068         0   2005068   0% /run/shm
none              102400         4    102396   1% /run/user
/dev/sdb1      488384532 110877248 377507284  23% /media/vasa1/TOSHIBA EXT
09:48 PM ~ $ 

```

---

### Post by matt_symes on 2015-07-23
Hi

> **vasa1 said:**
> I'm trying to understand hard links (in the context of rsync).

I came across [this]("http://askubuntu.com/questions/108771/what-is-the-difference-between-a-hard-link-and-a-symbolic-link"):

But I'm using **rsync** with **--link-dest** to backup data (incrementally) from my laptop's hard drive to an external USB drive. [It seems to be working]("http://ubuntuforums.org/showthread.php?t=2287961"). But aren't two different file systems involved?

```
09:47 PM ~ $ df
Filesystem     1K-blocks      Used Available Use% Mounted on
/dev/sda6      219476804  14552800 193752116   7% /
none                   4         0         4   0% /sys/fs/cgroup
udev             1994280         4   1994276   1% /dev
tmpfs             401016      1232    399784   1% /run
none                5120         0      5120   0% /run/lock
none             2005068         0   2005068   0% /run/shm
none              102400         4    102396   1% /run/user
/dev/sdb1      488384532 110877248 377507284  23% /media/vasa1/TOSHIBA EXT
09:48 PM ~ $ 

```

You can only have hard links within the same filesystem. 

i.e. a file system that spans a whole disk or the filesystem in a partition or the file system in a mounted loop back device.

This is because hard links reference an inode and the same inode number can be used accross different file systems. This would make resolving hard links across filesystems impossible using the current hard link implementation method.

Soft links suffer none of these problems as they do not reference the inode directly but use a string to reference the files path. This allows them to span filesystems.

What rsync is doing when creating an incremental backup is referencing the existing destination backup against the source directories to backup and creating the hard links on the destination backup when the file exists and has not been modified.

Kind regards

---

### Post by vasa1 on 2015-07-23
> **matt_symes said:**
> ...

What rsync is doing when creating an incremental backup is referencing the existing destination backup against the source directories to backup and creating the hard links on the destination backup.

Kind regardsSo **all** of the hard links are on the USB drive in my case, the destination backup. Thanks for the explanation :)

---

