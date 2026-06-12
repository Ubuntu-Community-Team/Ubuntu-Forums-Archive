---
title: "gparted"
date: 2013-03-01
forum: General Help
---

### Post by tombull50 on 2013-03-01
A friend an old lady let her grandson use her laptop and of coarse by the time he was finished the computer was infected and unusable.
No one could fix her computer, she paid someone money too so I voluntered to try. I installed the lates verson of Ubuntu i386 a few weeks ago and it works fine, but the old lady can't deal with "something" different" since it is not windows she still cannot use her computer.
OMG I hate windows but she wants me to reinstall windows on this computer.
Windows will not install because it cannot find a compatable disk or something like that.
I cannot get gparted to wipe the drive because it is "active" so I try to umount.

pat@pat-MX8739:~$ sudo umount /dev/sda1
umount: /: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

Why can't I just pop in a windows disk and install windows?
How can I wipe this active drive and install windows?

---

### Post by plucky on 2013-03-01
Boot a Live CD or USB and turn off swap and you will be able to delete all your partitions.


Good Luck

---

### Post by tombull50 on 2013-03-01
Thanks I'll try that.

---

### Post by grahammechanical on 2013-03-01
I guess this > [COLOR=#000000]Windows will not install because it cannot find a compatable disk or something like that.[/COLOR] means that the format of the partition is incompatible with Windows. Does it not give you the option to format the drive? Are you sure it is a Windows install disk and not a recovery disk?

Regards.

---

