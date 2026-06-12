---
title: "Having trouble with USB device mounting behavior"
date: 2007-06-26
forum: General Help
---

### Post by FrozenFOXX on 2007-06-26
I'm having a small problem and I'm not entirely positive how to fix it.  

**The short version**
My USB hard drive does not use the default mount point I want it to.

**Long version**
I have an external hard drive in an external enclosure (converted a 40GB internal IDE drive to an external USB/Firewire drive).  The drive itself works great and has been formated with ext3 (single volume).  No issues there.

What I'd LIKE to do is have this drive, whenever plugged into my system, to be mounted to a directory I created, /media/externbackup instead of anywhere else.  I would also like it owned by root, have the group set to "staff," and have the permissions 770 (rwxrwx--- so NOBODY but those on the members of staff and root can even go into it...very, VERY important).


I have added the following entry to the bottom of my otherwise stock /etc/fstab.
[quote=/etc/fstab]
# /dev/sda1
UUID=5fad2e08-cd97-4cbe-aeef-3271baad1406 /media/externbackup  ext3 defaults,noauto 0 0
[/quote]
So, to my understanding, whenever the device is plugged in (as that is its UUID) it should be mounted to /media/externbackup.


Here's my problem.  Whether I leave it plugged in at bootup or plug it in during normal use it automatically mounts the drive to /media/usbdisk.  This is strange since I can't find out why it would ignore the fstab and mount it somewhere else.

To solve the permissions and ownership issue (since having any old user account able to read any part of a full system backup would be a perilous proposition indeed, even with its own permissions in place) I mounted the disk via "$sudo mount /media/externbackup/" and did a sudo chmod 770 ; sudo chgrp staff to it.  Whenever I mount it, even if it's automatically mounted to /media/usbdisk, it maintains these permissions and ownership (I'm going to assume it's actually on the disk filesystem but please feel free to enlighten).

I run Kubuntu normally but I have Xubuntu installed on the same system and it exhibits the same behavior.  I've also tried using KDE's automounting settings in the Properties dialog for the device to no effect.  No matter what, when you plug it in it mounts to /media/usbdisk and completely ignores the /etc/fstab.



So, anyone have any idea how to stop it being automatically mounted to /media/usbdisk?  After modifying the fstab to tell it where I want to be able to mount it I'm not really sure what else to change since I'm not familiar with Ubuntu's automounting.  Is there something else I need to change?  I'm having a feeling this has something to do with HAL but I've yet to find anything about exactly how Ubuntu handles automounting.

---

