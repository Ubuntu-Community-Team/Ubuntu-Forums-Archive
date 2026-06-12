---
title: "Can't Mount External Drive (&quot;/dev/sdb1 does not exist&quot;)"
date: 2008-04-16
forum: General Help
---

### Post by Weezer on 2008-04-16
I have a Western Digital "My Book" USB external hard drive.  When I boot into Ubuntu with it plugged in, it is automatically mounted, and I can use it as I would on my Windows partition. If I type boot -l in the terminal, I can determine its location to be /dev/sdb1 and it is (obviously) being mounted to /media/My\ Book. However, if the hard drive stops spinning (which it does if it is unused for about thirty seconds), then it is unmounted and I cannot remount it: Typing mount /dev/sdb1 /media returns that /dev/sdb1 does not exist.

This has happened every time but once, and after testing to see if it would continue working, it reverted back to its old "special device /dev/sdb1 does not exist".  A friend suggested ACPI issues might be a probable cause. Any ideas on how to get this drive to mount without rebooting? 

Thanks for your help.


Oh yeah, if it's of any interest, I'm running Ubuntu 7.10 on a Lenovo T61p laptop.

---

### Post by kyphi on 2008-04-16
Your USB drive should work the same way as any other USB device.

You do not boot your computer with the drive attached but attach it after your computer is running.

Check that the following is set correctly:

Go to System, Administration, Users and Groups.  Find your login name on the list, click on it and then activate the Preferences menu.  Go to User Privileges and place a tick in the box that says "enable access to external storage devices automatically".

---

### Post by Weezer on 2008-04-17
Hmm, I've just realized that the drive only stops working after having started rhythmbox music player. "Removed device to prevent data loss". 

I suppose I'll try a different music player and see if it helps.

---

### Post by Weezer on 2008-04-18
No luck there, either. Seems to do it after enough idle time.

---

### Post by kyphi on 2008-04-19
Do you have gnome screensaver enabled ?  If so, disable it completely and see if that makes a difference.

USB devices can be problematic.  There are many stories on the net about flashdrives that will not load in one computer but will function perfectly in another.  I have experienced this myself but do not know the cause nor the remedy YET.

I use a Maxtor Mini 60 GB USB drive for backups which has worked well so far.  It requires 2 USB connections.

Also, try the USB ports at the back.

---

