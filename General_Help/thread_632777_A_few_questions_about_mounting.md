---
title: "A few questions about mounting"
date: 2007-12-05
forum: General Help
---

### Post by jbru on 2007-12-05
So I've tried man page's, google, forum searching and I can't seem to find the answer to my problems.  I figured I'd better stop in for help before I break something.

So far I've managed to successfully mount two hard drives.  One internal Ext3 drive and one external ntfs drive.  I've used similar options in fstab for both drives, but they mount with different security settings (the big difference is that I set the ntfs drive to read only, and the ext3 drive to read/write).

Before you get ahead of me here, the security settings are not what you think.  For some reason, the ntfs drive allows full read/write access to all users, while the ext3 drive requires root privileges to do anything with it.

The lines i've used to mount each drive is:
```
sudo mount /dev/sdb1 /home/admin/mnt/sdb1
sudo mount /dev/sdc1 /home/admin/mnt/jenny 
```

My fstab looks like this with the two important entries at the bottom:
```
# /etc/fstab: static file system information.

#

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0

# /dev/sda1

UUID=37a7efce-9ee9-4ad7-975a-5402ba64d607 /               ext3    defaults,errors=remount-ro 0       1

# /dev/sda5

UUID=8507e63f-2961-46d7-8f64-a4115a53fea2 none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0



# /dev/sdb1 this drive is ext3

UUID=206f5b9f-00b1-4a4d-b1d5-617c2acf946c	/home/admin/mnt/sdb1	ext3	rw,user,noauto,exec,sync	0	0



# /dev/sdc1 this drive is ntfs

UUID=B26218B2621288	/home/admin/mnt/jenny	auto	ro,user,noauto	0	0
```

and ls -al in the directory they are mounted it produces this:
```
total 8

drwxrwxrwx 1 root root 4096 2007-12-05 20:29 jenny
drwxr-xr-x 3 root root 4096 2007-12-05 20:34 sdb1
```

What is it that I'm doing wrong?
I would like to be able to remove the 'noauto' option and automatically mount ext3 with read/write options for users and the ntfs drive with read only capabilities?

---

### Post by ccprog on 2007-12-05
For the ntfs drive, you need to add the option umask=444

The ext3 drive actually does exactly what you wanted. The options are not about user privileges for things inside the drive, but only about mounting privileges. You have to give r/w acess in a separate process.with chmod.

---

