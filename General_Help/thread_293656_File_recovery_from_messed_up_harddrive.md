---
title: "File recovery from messed up harddrive"
date: 2006-11-05
forum: General Help
---

### Post by bobpur on 2006-11-05
I had a Seagate 80 gb drive installed as additional storage on a computer that I was putting Ubuntu on for a dualboot setup. I'm not sure how it happened, the install put some files (maybe grub?) on the drive that won't let me access it from windows. I have to disconnect it to boot in windows. It gives a boot error in grub (17 or 21)unless I disconnect it.
I can see the files from a linux distro (Ubuntu Dapper & MEPIS) but I can't touch anything but a couple pictures and can't delete the offending grub(?) files.
I don't want to lose the stuff on the drive as it has months of accumulated linux stuff (Distro ISO's,howto's, plus assorted picture, music and freeware files)
I'll wipe it to get the drive back if I have to, but I want to exhaust a few more options first before I wipe it
As always, help is appreciated. Thanks.

---

### Post by justifier on 2006-11-05
try editing the nessicary files using a live CD

---

### Post by aysiu on 2006-11-05
> **bobpur said:**
> 
I can see the files from a linux distro (Ubuntu Dapper & MEPIS) but I can't touch anything but a couple pictures and can't delete the offending grub(?) files. Try Alt-F2 and ```
gksudo nautilus
``` in Gnome or ```
kdesu konqueror
``` in KDE. That should allow you to delete whatever you want.

---

### Post by bobpur on 2006-11-05
Thanks for the responses. It'll give me something to do this evening.

---

