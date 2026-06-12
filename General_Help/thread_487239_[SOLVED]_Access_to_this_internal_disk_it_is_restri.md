---
title: "[SOLVED] Access to this internal disk it is restricted to system administrators for.."
date: 2007-06-28
forum: General Help
---

### Post by Super TWiT on 2007-06-28
I repartitioned my hard drive so I could use the disk as a Mythtv video storage area.  Its formatted as an ext3 file system.  When I try to mount it in Ubuntu I need an administrator password to mount it.  This is somewhat inconveniencing to have to put in the password every time I mount the drive.  I would like it to mount just like another partition.  Is this possible to do without reinstalling Ubuntu?

---

### Post by PilotJLR on 2007-06-28
Yes - by adding the "user" tag to the partition in /etc/fstab, an ordinary user can also mount it. More details here:
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by Super TWiT on 2007-06-28
Thanks for replying!:p  At this point, it is recognized as /media/disk and isn't in fstab.

---

### Post by Super TWiT on 2007-07-06
I figured out how to add it to fstab and it works now!:D  Thanks for the reply!

---

