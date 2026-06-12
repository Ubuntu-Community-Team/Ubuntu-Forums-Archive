---
title: "No CD Icon appears on desktop!"
date: 2008-02-10
forum: General Help
---

### Post by BeauMN on 2008-02-10
I'm having trouble getting the CD icon to appear on the desktop.

It's weird... If I put in an Audio CD, the icon appears.  But if I put a Data CD in, there is no icon.  It still mounts... I can access the contents through /media/cdrom/  But no desktop icon.  Any idea what may be wrong?  I'd like to be able to right-click so I can easily copy the disc to an image, but this is interfering.

I'm runnin 7.10 on a Dell 600m laptop.  I haven't changed much since the initial install, just some updates and installing a few packages, but no major configuration changes.

If any extra info from me could help you to help me, just let me know.

Thanks!

---

### Post by SonicSteve on 2008-02-18
I believe that Gutsy has a bug regarding Icons of mounts. For me it usually happens with network share mounts.

I doubt that this is your issue but since you mount some types of CD media and not others but...
There seems to be a bug regarding mounts made in the /mnt folder not being added to Nautilus, desktop etc. If you mount in the /media folder it shows up properly. 
Do you now how to edit your FSTAB configuration file? Make sure that your mounts are mounting in /media and not /mnt. Again I doubt that this will help but check it out.

---

