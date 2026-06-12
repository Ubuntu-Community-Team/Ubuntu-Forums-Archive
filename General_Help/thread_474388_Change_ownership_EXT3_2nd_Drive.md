---
title: "Change ownership EXT3 2nd Drive"
date: 2007-06-15
forum: General Help
---

### Post by turtleJP on 2007-06-15
Ok, I've gone in and formated the drive with gparted. Rebooting and looks great except for the problem that I can not write to the drive. This is not an NTFS drive so that route isn't going to cut it. Windows be gone! 


Any ideas to get the ownership back to the group so all users can use the drive. Heck I'd settle for just me at the moment but it's a family computer. 

Thanks in advance,

TurtleJP

:D

---

### Post by straps on 2007-06-15
For my experience, GParted can only make partition, it doesn't format it

From the terminal:

Assuming that the new partition is /dev/sdb1, you have to create the Filesystem with
**sudo mkfs.ext2 /dev/sdb1**

Mount it
[B]sudo mkdir /mnt/sdb1
sudo mount /dev/sdb1 /mnt/sdb1[/B]

Change the Ownership
**sudo chown user:group /mnt/sdb1**
change user:group with the user and group you want

And optionally change permissions
**sudo chmod XXX /mnt/sdb1**
change XXX with the permission flag you want

And it should work well...

Let me know, bye

---

### Post by straps on 2007-06-15
To format it as ext3, the first command should be
**sudo mkfs.ext3 /dev/sdb1**

bye

---

### Post by turtleJP on 2007-06-15
Yep, gparted does actually format the drive. And chown worked like a charm :) 

The only thing that is a bit off is that the drives are not automouting at login.


Thank you,
TurtleJP

---

### Post by Mr. C. on 2007-06-15
Add them to your /etc/fstab.

MrC

---

