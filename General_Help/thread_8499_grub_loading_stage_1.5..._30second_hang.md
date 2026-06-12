---
title: "grub loading stage 1.5... 30second hang?"
date: 2004-12-18
forum: General Help
---

### Post by Renners on 2004-12-18
Hi,

This is a problem I've had with GRUB on every Linux distro I've tried. I've asked in many forums but no-one seems to know the answer! One more try now that I've settled for Ubuntu...

Basically, GRUB waits for 30 seconds at the "loading stage 1.5" bit, before presenting the boot menu. (on some distros it's "loading stage 2"). 30 seconds doesn't sound long but it becomes annoying after a while!

LILO doesn't hang like this, only GRUB. My system is a standard desktop PC, with no strange hardware attached, dual booting with winXP.

ne1 know why this might be happening? Or are there any log files or perhaps a verbose option for GRUB so that I can see what it's waiting for?

Thanks, Renners.

---

### Post by jonrkc on 2005-08-23
[QUOTE=Renners]Hi,

This is a problem I've had with GRUB on every Linux distro I've tried. I've asked in many forums but no-one seems to know the answer! One more try now that I've settled for Ubuntu...

Basically, GRUB waits for 30 seconds at the "loading stage 1.5" bit, before presenting the boot menu. (on some distros it's "loading stage 2"). 30 seconds doesn't sound long but it becomes annoying after a while!

LILO doesn't hang like this, only GRUB. My system is a standard desktop PC, with no strange hardware attached, dual booting with winXP.

ne1 know why this might be happening? Or are there any log files or perhaps a verbose option for GRUB so that I can see what it's waiting for?

Thanks, Renners.[/QUOTE]
 I came across this thread in a search for the solution to the same problem.  If it's any clue, I only started having this problem today after one of my three hard disks failed.  I removed it from /etc/fstab, and it is not in any way involved in the boot process, and contains only backup files.  Or used to contain them!  

I'd say the hanging time on my system is more like a minute.  Then it goes on with no error messages at all.  And at normal speed.

---

### Post by jjjjjjj on 2006-10-19
I have installed at least 3 different distros and the last one here of xubuntu finally installed but hangs at the GRUB for 3 minutes.
I'm convinced this is a sign of a failing drive.  The pc in question had a windows 2000 install go south so I threw linux on it  and now am experiencing this.  Ran western digital tools till the cows came home with no errors?  controller maybe?  thanks

---

