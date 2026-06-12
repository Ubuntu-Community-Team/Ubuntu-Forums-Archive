---
title: "usb thumb drives won't mount"
date: 2007-03-30
forum: General Help
---

### Post by kpjoyce on 2007-03-30
when I plug in my usb thumb drives, the system doesn't mount them automatically. They show up in /dev and in 'places', but when I click on them I get an error message that says only root can mount /dev/sda1.  I can mount the drive in terminal using sudo, but then it is read-only (maybe a different problem?)
I have a new and pretty standard install of 6.06.

Any ideas how I can get this to work for me?  I appreciate your help.

---

### Post by Ramses de Norre on 2007-03-30
Is **gnome-volume-manager** enabled in your start up programs? (system>preferences>sessions)

---

### Post by kpjoyce on 2007-03-30
Thank you for your reply.

Yes, that entry is in 'Startup Programs'.  The command listed is 'gnome-volume-manager --sm-disable'.

---

### Post by MikeDX on 2007-03-30
Is it at all possible these drives are ntfs?

---

### Post by kpjoyce on 2007-03-30
NTFS?  No ... that's a good thought, but all of the drives use the vfat filesystem.

---

### Post by MikeDX on 2007-03-30
is it possible for you to try a live cd of edgy and see if you get any further? I have never had any hot swapping problems running usb sticks or memory cards on my edgy installs.

---

### Post by kpjoyce on 2007-03-30
Here's some more interesting wrinkles I just discovered with more playing:  It seems that only the first drive plugged in has the problem.  Subsequent drives mount just fine.  Could the problem be limited to drives labeled 'sda'?

Also, I happen to know that everything worked fine with edgy.  I had an edgy install that had no problems with this, but I ditched it for my Dapper install b/c of other issues.

---

### Post by linuksas on 2007-04-01
> **kpjoyce said:**
> when I plug in my usb thumb drives, the system doesn't mount them automatically. They show up in /dev and in 'places', but when I click on them I get an error message that says only root can mount /dev/sda1.  I can mount the drive in terminal using sudo, but then it is read-only (maybe a different problem?)
I have a new and pretty standard install of 6.06.


You have to go to System->Administration->Users, click your user name, then on properties->advanced (last tab), there you have several boxes and find one where it says "automatic mount when I plug usb ..."

then reboot

I write this as I recall in my memory becouse I'm not near my comp and I write this over WinXP, so I'm not sure if it 100% what you need.
I hope it will help.
Peace

---

