---
title: "Autofs doesnt seem to work, please help :-("
date: 2008-03-23
forum: General Help
---

### Post by rflook on 2008-03-23
Hi,

I am currently using MythBuntu (Gutsy) and am having a problem automounting my external USB harddrive with autofs. As my ext HD has all my music on it i want to automount it to /var/lib/mythtv/music (the default location for music). I used to used Knoppmyth and figured the process would be the same, so i editted my /etc/auto.master file to include the line

/var/lib/mythtv/music /etc/auto.removable --timeout=2

and then editted the auto.removable file to include the line

usbdrive -fstype=vfat,rw,uid=1000,umask=022 :/dev/sdb1

Now even when restarting my computer or restarting autofs by running /etc/init.d/autofs restart it doesnt appear to automount. Can anyone help me with this?

Many thanks

Rob

---

### Post by rflook on 2008-03-23
Hmm, 

Have found out something interesting, if i run 

ls /var/lib/mythtv/music 

then i get a blank return, but if i run

ls /var/lib/mythtv/music/usbdrive

then it shows the directory listing of the usb drive. Thing is when i run mythtv it doesnt pick up the tunes in that directory. So how can i force ubuntu to see the drive i mounted.

---

