---
title: "auto mount sda2 vfat drive on startup?"
date: 2006-10-13
forum: General Help
---

### Post by strabes on 2006-10-13
I am dual booting windoze and ubuntu. sda1 is windows ntfs, sda2 is vfat partition for sharing files between windows and linux and is called "data", sda3 is my filesystem, and sda4 is my /home partition. My problem is that sda2 mounts when I startup, but it is owned by the root user. So, I have to do 

sudo umount /mnt/data
mount /mnt/data

in a terminal whenever I start up my computer in order to be able to write to this partition. I want these two commands to be executed on startup so that I dont have to keep typing them in all the time. Thanks for any help. Here is my fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda4       /home           ext3    defaults        0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda2	/mnt/data	vfat	rw,user	        0	0

```

---

### Post by kidders on 2006-10-13
Hi there,

What you probably want to do is this:

[LIST=1]
[*]Type **echo $UID** to find out what your user ID is.
[*]Type **cat /etc/group|grep ^`whoami`** to find out what the GID for your primary group is. The output will probably look something like "groupname:x:GID:".
[*]Take the "user" option away from your /dev/sda2 line in /etc/fstab. (This will prevent anyone but root from dismounting the filesystem, which is normal.)
[*]Add **uid=1234,gid=2345** to the options for /dev/sda2, where 1234 is your UID and 2345 is your primary GID.
[/LIST]

You'll wind up with something like:
```
/dev/sda2		/mnt/data		vfat		uid=1234,gid=2345,noexec        0 0
```

That should have the effect of making you the owner of all files on the volume. You might also like to check out the "umask" and "dmask" directives, that let you set the permissions of files & directories in the filesystem.

Hope that helps.

---

### Post by strabes on 2006-10-13
thanks for your help, although I already found the solution on ubuntuguide.org. That guide is really amazing. Thanks again.

---

