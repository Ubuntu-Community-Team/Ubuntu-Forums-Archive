---
title: "Owning a partition"
date: 2006-11-29
forum: General Help
---

### Post by gareththegeek on 2006-11-29
I seem to be getting a number of problems recently with my windows partition and ownership.  I have a partition which I use to share data between windows and linux.  It is formatted to fat32 and mounted using the fstab file.  However the partition is owned by the root user and this seems to cause various problems with certain pieces of software, for example azureus says it can't set the file length of files when I use the partition but works fine if I download to my home folder...

Are suggestions how I can resolve this?  Is there any way that I can own the partition myself?

fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda2	/media/sda2	vfat	iocharset=utf8,umask=000	0	0

The partition is sda2.

Thanks,
G!

---

### Post by taurus on 2006-11-29
You can try something like (from a terminal)

```
sudo chown -R gareththegeek:gareththegeek /media/sda2
(assuming gareththegeek is your login name!!!)
```

---

### Post by gareththegeek on 2006-11-30
Thanks for the suggestion but I get the following error

gareth@gareth-desktop:~$ sudo chown -R gareth:gareth /media/sda2
chown: changing ownership of `/media/sda2/programming/archive.rar': Operation not permitted

etc etc for every file

or

gareth@gareth-desktop:~$ sudo chown gareth:gareth /media/sda2
chown: changing ownership of `/media/sda2': Operation not permitted

Any more ideas? Or would it have been better to somehow set my home folder to this partition (can I do that?)

Thanks
G!

---

### Post by mbeierl on 2006-11-30
You want to use the uid and gid options for mount in fstab, which tell the operating system who the "owner" of the files should be for the "ownerless" fat32 filesystem.

Something like this:

```
/dev/sda2 /media/sda2 vfat iocharset=utf8,umask=000,uid=1001,gid=1001 0 0
```

(provided your uid is 1001, and your gid is 1001)

---

### Post by gareththegeek on 2006-12-03
Thanks!

That did the trick,
G!

---

