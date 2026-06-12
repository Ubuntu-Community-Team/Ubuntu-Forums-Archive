---
title: "Your session only lasted less than 10 seconds"
date: 2007-10-07
forum: General Help
---

### Post by bishounen on 2007-10-07
ok,

I started randomly getting this error about a week ago.  I've gone through ALL the similar threads on this issue (yay for a really good search function!  Well done Ubuntu forum designers.)  and none of them seemed to apply to my situation, but I tried several of the solutions that seemed like they might work.  No luck.

Fortunately I had all my important files and bookmarks backed up (thank you Foxmarks plugin.) so I booted using the Live CD, formatted the Ubuntu partition on my dual-boot box with Gparted and reinstalled a fresh copy of Feisty onto the blank partition.

Once the install was complete I rebooted, selected Ubuntu from the boot menu and logged in.

BANG!  Same message again!  So now I'm REALLY confused.  I know it's not a space issue, since it's a 100 GB partition I installed it onto.  All the hardware is working normally as far as I can tell, and I am having no issues on the Windows partition (yes, I know they work differently, but if there is a hardware problem, it will usually show up in Windows too).

Here's the weird part.  After booting into Windows for awhile to do some stuff there, I rebooted into Ubuntu and NO ERROR.  So I ran a full system update (still haven't  touched ANYTHING in my new installation.) and rebooted after the update and BAM!  right back into the error window again.  Here's the full text of the logs:

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "username"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/Yuzuki:/tmp/.ICE-unix/5258

(gnome-volume-manager:5329): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(nautilus:5325): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-panel:5322): GnomeUI-WARNING **: While connecting to session manager:
IO error occured doing Protocol Setup on connection.
```

I did change my username in the text above to "username", but other than that this is the full text of the log.

Anyone have ANY CLUE what is happening here?  The only thing I can figure is that I have a bad sector on the hard drive and it's causing Ubuntu to choke and/or have problems during the session startup process.  If that's the case I can easily replace the drive since it's a separate one from my Windows drive.  If not then I'm really concerned.

Help!

---

### Post by bishounen on 2007-10-07
Ok, nevermind.

I booted into Windows recovery console and ran a chkdsk -R on the secondary drive that was holding Ubuntu.  It found not just one, but several bad sectors on the drive.  So it looks like that was the issue, several very small faulty sectors corrupting the data.  I reset my PC to boot directly into Windows and will be pulling the faulty drive for replacement.  I guess I'll just wait for Gutsy Gibbon to finalize and then I will reinstall Ubuntu again.

Thanks anyway!

---

### Post by magnj on 2008-02-05
I have the same issue with 7.1 server.  The previous OS was windows, I go the PC from a friend and it was blue screening before login.  This leads me to believe the drive is bad, I'll have to check later :(

---

