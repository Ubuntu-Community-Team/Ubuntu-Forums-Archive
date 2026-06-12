---
title: "yet another 1400x900 resolution issue"
date: 2007-12-25
forum: General Help
---

### Post by orlox on 2007-12-25
Hi all, and merry Christmas!

I just aquired a widescreen monitor (lg flatron wide model M198WA-BM) but I cant get it to work on its optimun resolution on ubuntu 7.10, 1400x900 (I cant even get it to work on any wide resolution)

I've tried using the GUI option under system->administration, but with no result. Also tried dpkg-reconfigure xserver-xorg several times....Even tried 915resolution to no avail...

---

### Post by logos34 on 2007-12-25
how about:

sudo apt-get install xserver-xorg-video-intel 

Reboot.

Check sys>admin>screen res for new modes

anything?

---

### Post by orlox on 2007-12-25
already installed that package to no avail...Also, when I tried 915resolution I got this strange message:

pablo@ubuntu:~$ sudo 915resolution -l
[sudo] password for pablo:
Intel 800/900 Series VBIOS Hack : version 0.5.3

Unknown chipset type and unrecognized bios.
915resolution only works with Intel 800/900 series graphic chipsets.
Chipset Id: 3141106

---

### Post by TidusBlade on 2007-12-25
It's possible that your Graphics card dosen't support that certain resolution, though unlikely...

---

### Post by orlox on 2007-12-25
This same pc, running under windows (but with a different monitor) allowed me to get higher screen resolutions

---

### Post by TidusBlade on 2007-12-25
Oh, then my last guess would be Graphics drivers and Monitor drivers...

---

### Post by dcstar on 2007-12-25
> **orlox said:**
> Hi all, and merry Christmas!

I just aquired a widescreen monitor (lg flatron wide model M198WA-BM) but I cant get it to work on its optimun resolution on ubuntu 7.10, 1400x900 (I cant even get it to work on any wide resolution)

I've tried using the GUI option under system->administration, but with no result. Also tried dpkg-reconfigure xserver-xorg several times....Even tried 915resolution to no avail...

[http://ubuntuforums.org/showthread.php?t=370204](http://ubuntuforums.org/showthread.php?t=370204)

---

