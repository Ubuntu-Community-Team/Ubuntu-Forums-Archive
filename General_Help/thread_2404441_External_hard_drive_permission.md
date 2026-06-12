---
title: "External hard drive permission"
date: 2018-10-24
forum: General Help
---

### Post by Singularity64 on 2018-10-24
My external hard drive shows up as fuseblk (NTFS partition I assume)  on Ubuntu when I plug it in the USB port. The disk is automatically mounted and the default permissions are read, write and execute for everyone (i.. 
e., 777).

Now as others have noted, merely issuing the command chmod does not change the permissions. Problem though is that even if I try to mount or remount the device, I am getting an error (the reason being that the device is mounted as soon as it is plugged in).

Any idea of what needs to be done to change the permissions on the drive? Thanks

Although I have scoured previous threads on topics related to external  hard drive permissions, I couldn't resolve my issue with suggestions from any  of them

---

### Post by yancek on 2018-10-24
LInux owner/permissions are not used/understood by windows filesystems.
Which Ubuntu release are you using?
Which windows release?
What is the error you are getting?
Do you have an entry in /etc/fstab for the windows partition?  If so, post it.
Are you trying to access the partition as a normal user or with root permissions (using sudo)?  A normal user will not have write access to much of anything outside his/her /home/user directory.

---

### Post by Singularity64 on 2018-10-25
I am accessing the drive with Ubuntu not Windows. 
 As I had said earlier, my problem is that the drive mounts with all permissions (read, write, execute) being available to *ALL* users.

---

### Post by yancek on 2018-10-25
> I am accessing the drive with Ubuntu not Windows. 

I"m fully aware of that, you weren't asked anything that would imply different.

If the drive mounts on boot, unmount it.  I asked you 5 questions and you answered one.  How about answering the other 4?

---

