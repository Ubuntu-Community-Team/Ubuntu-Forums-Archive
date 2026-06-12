---
title: "can not eject"
date: 2007-07-08
forum: General Help
---

### Post by dennus on 2007-07-08
I have an external USB DVD/COMBO. It is mounted in fstab with the following line...

#/dev/scd1
/dev/scd1 /media/dvdrom iso9660 defaults 0 2

Now, my problem is I can not EJECT the disk, or even open the drive, when I'm using my regular account.  I can, temporarily solve this by entering  sudo eject dvdrom in the terminal. But I want to be able to do this without entering my root password. How should I mount it the proper way?

---

### Post by boralyl on 2007-07-08
When a disk is loaded doesn't an icon appear on your desktop with the CDRom Drive?  You can right click that icon and choose Eject.

---

### Post by bettlebrox on 2007-07-08
Either change your fstab to this:

[INDENT]/dev/scd0       /media/cdrom0   

To this:

[INDENT]/dev/scd1 /media/dvdrom udf,iso9660 user,noauto     0       0[/INDENT]

Or, comment it out from /etc/fstab and see if Gnome will automount it for you with the right permissions.

Luck

---

