---
title: "Xubuntu filesystem unknown"
date: 2007-04-26
forum: General Help
---

### Post by GabrielWolff on 2007-04-26
After probably over loading my HD, I'm unable to log in.
With the live CD gparted is unable to determine my hda6 filesystem.
How do I find it out? 
I most probably only have to mount hda6 and delete a few files to fix it all...

G

---

### Post by indytim on 2007-04-26
Why not boot to your LiveCD (assuming you did not do the alternative install), mount hda6 and have at it with deleting files?

IndyTim

---

### Post by GabrielWolff on 2007-04-26
> **indytim said:**
> Why not boot to your LiveCD (assuming you did not do the alternative install), mount hda6 and have at it with deleting files?

IndyTim

Well, I think that's what I tried to do.

But when opening a terminal while the machine is running the live CD and trying to mount results in the system stating that I specified a wrong file system:

[PHP]ubuntu@ubuntu:~$ sudo mount -t vfat /dev/hda1 a
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/PHP]

The question is: what do I replace the *vfat *with, or: How do I find that out?

G

---

