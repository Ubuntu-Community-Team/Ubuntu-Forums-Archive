---
title: "Grub taking ages"
date: 2007-08-16
forum: General Help
---

### Post by Black_Monkey on 2007-08-16
When I boot up my PC, grub takes 3 or 4 minutes to start, much more than kubuntu does. Is this normal? If not, any ideas how to fix it, and if it is, are there fast boot managers? Lilo?
Just that on my Windows PC, I'm into the OS in no time.

---

### Post by janarene on 2007-08-16
No - it's not nearly normal for Grub to do that.  My first thought; Do you have a CD in your drive that the computer is attempting to boot from and finally failiing before trying the hard drive?

---

### Post by kellemes on 2007-08-16
Grub should load in seconds..
I have the same thought as previous poster.. maybe you can disable some bootdevices in BIOS, could be he's looking for devices that are not there.. Also check bootorder.

---

### Post by geek2330 on 2007-08-16
I had the same issue sometime ago and couldn't find help here after many posts.
After troubleshooting extensively, if I leave a CD in the cdrom bay, can be a blank cd, then the boot process was really much better, from 3 minutes or so to about 1 minute.

Note that my cdrom was NOT chosen as the 1st bootable device, it was my Kubunty drive but it looked as if Ubuntu wanted to "see" a media in the cdrom drive, regardless if it was blank or not.

.

---

### Post by Black_Monkey on 2007-08-16
The harddrive is first in the boot list. Thanks for that suggestion geek2330, I'll give that a try.

---

### Post by Black_Monkey on 2007-08-26
*bump*

I tried putting a CD in the drive, and it made no difference - does anyone else have any ideas? It was the same when I had FC5, and I completely wiped the disk to install Kubuntu.

---

### Post by Black_Monkey on 2008-02-20
This is really bugging me, still haven't found a solution to this. Any ideas?

---

