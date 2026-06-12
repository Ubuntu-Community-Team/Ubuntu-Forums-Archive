---
title: "e2fsck aborts on mounted file system in Ubuntu 8.04"
date: 2008-06-15
forum: General Help
---

### Post by antti64 on 2008-06-15
Hi!

I just upgraded my fine working Ubuntu 7.10 into 8.04.

I met following problem with e2fsck.  

>> more /var/log/fsck/checkfs

Log of fsck -C3 -R -A -a
Sun Jun 15 14:40:47 2008

fsck 1.40.8 (13-Mar-2008)
/dev/sda1 is mounted.  e2fsck: Cannot continue, aborting.

/dev/sdb1: clean, 12667/16777216 files, 5530205/33523630 blocks
/dev/sdb3: clean, 9019/2513280 files, 3869768/5024328 blocks
fsck died with exit status 8

Sun Jun 15 14:40:48 2008
----------------

Why Ubuntu 8.04 runs e2fsck for already mounted file system during the system boot?

There is nothing wrong with /dev/sda1. I run e2fsck from separate boot disk to be sure. Problem appreared with 8.04.

Is this related into 8.04 automount problems?

[http://ubuntuforums.org/showthread.php?t=771835](http://ubuntuforums.org/showthread.php?t=771835)

Thanks, 

Antti

---

### Post by antti64 on 2008-06-16
> **antti64 said:**
> Hi!

I just upgraded my fine working Ubuntu 7.10 into 8.04.


Antti

Let's ask it simpler. Do I really need /etc/fstab anymore in Ubuntu 8.04?
I have root file system in internal PATA harddrive and /home internal SATA harddrive?

Antti

---

### Post by plucky on 2008-06-16
> Let's ask it simpler. Do I really need /etc/fstab anymore in Ubuntu 8.04?
I have root file system in internal PATA harddrive and /home internal SATA harddrive?


Q1 - Yes

Q2 - It is how the system knows where to mount your partitions.


The question you should be asking is why is fsck trying to run on a mounted partition?

Can you post the output of ```
cat /etc/fstab
cat /boot/grub/menu.lst
sudo fdisk -l
```

---

### Post by chrisccoulson on 2008-06-16
You should never run fsck on a mounted volume. It is very likely to break it, especially if any write accesses happen to the disc during the scan. 

Refer to 'man e2fsck'
> Note that in general it is not safe to run e2fsck on mounted filesystems. The only exception is if the -n option is specified, and -c, -l, or -L options are not specified. However, even if it is safe to do so, the results printed by e2fsck are not valid if the filesystem is mounted. If e2fsck asks whether or not you should check a filesystem which is mounted, the only correct answer is ''no''. Only experts who really know what they are doing should consider answering this question in any other way. 

*Edit: Sorry, I just re-read your post and realise that you're not deliberately runnig e2fsck on the mounted disc*

---

### Post by antti64 on 2008-06-17
> **plucky said:**
> Q1 - Yes
Q2 - It is how the system knows where to mount your partitions.


Thanks, I thought something has changed in Ubuntu and /etc/fstab is obsolete. 

> **plucky said:**
> 
The question you should be asking is why is fsck trying to run on a mounted partition?


That is what I was also wondering. 

> **plucky said:**
> 
Can you post the output of ```
cat /etc/fstab
cat /boot/grub/menu.lst
sudo fdisk -l
```

My /etc/fstab _HAD_ :

/dev/sda1       /home           ext3    defaults        1       2
# /dev/sda1
UUID=00103ddc-1855-4021-ba2d-dde333605e4f /media/sda1     ext3 defaults        0       2

So, /dev/sda1 was mounted twice. Mount as /media/sda1 isn't really necessary. It had just been there, but never causing problems. 

I realised, Ubuntu 8.04 is possibly first mounting /dev/sda1 as /home and then running e2fsck for mounted partition. Therefore, I removed "2" from the column of the second mount. So far, it seems to work. I haven't had "routine check of harddrives yet". 

Now my /dev/sda1 mounting in /etc/fstab looks this:

# This is my SATA containing /home
# Seems to map as /dev/sda1 in 8.04
UUID=00103ddc-1855-4021-ba2d-dde333605e4f /home           ext3    defaults      0       2

# /dev/sda1
UUID=00103ddc-1855-4021-ba2d-dde333605e4f /media/sda1     ext3    defaults      0       0

Antti

---

