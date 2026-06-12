---
title: "EAC with Wine in Edgy"
date: 2006-11-28
forum: General Help
---

### Post by joker on 2006-11-28
I am trying to get EAC (Exact Audio Copy) to run under wine in Edgy.  I installed wine using automatix2.  Edgy is a clean install.  EAC installs but will not recognise my CD Drive.  I have run winecfg and told wine it is a CD drive in the advanced drive options.  

I perviously had EAC running without issue under Dapper, I just followed the how to located in the forums.  Those directions do not seem to work under Edgy.  The option to use the native ASPI interface is greyed out and not selectable.  I tried installing an ASPI driver from Adaptec but it made no difference.

Even if you can't help with the problem, please let me know if you can use EAC under Edgy or if you are also having issues.

Thank You

---

### Post by Cable on 2006-11-28
I have EAC working perfectly in Wine.  When telling Wine that your CD drive is indeed a CD-ROM drive, be sure to have a CD in the drive, as it seems to "forget" if you don't for some odd reason.  In EAC, tell it to use the native SCSI interface for the drive.  That got EAC to recognize my drive and worked great.  Post again if you have more problems.

---

### Post by joker on 2006-11-28
Thank you for the reply, at least I know it can work.

I did have a cd in the drive when I configured wine and it is remembering the settings.

In EAC the native interface option is greyed out and not selectable.  My only choice is to use the installed external interface, which apparently doesn't exist.

I will try purging wine and EAC and starting over completely, I will post my results.

Thanks again.

---

### Post by joker on 2006-11-28
It works now!  

For anyone else who has this issue, here is what I did.

1) went into synaptic package manager
2) found the installed wine package and selected complete removal
3) deleted the .wine directory in my /home folder
4) install the same wine package I had just removed
5) insert cd into drive
6) run winecfg
7) under the drives tab select the cd drive, then the advanced tab, and set the drive type to be cdrom, apply and close
8) install EAC, start EAC
9) select native win32 interface in the EAC options menu
10) close and restart EAC
11) success

I had previously done all these things but not in this order, so if you also have trouble it is something to try.

Thanks again for the help.

---

### Post by iceolate on 2007-08-18
Joker, you're a hero! i did all those steps as well, but in a varying order, but i 
followed that exactly, and lo!

i've been having problems with ruby ripper, so maybe this'll work out for me.

cheers!

---

### Post by MetalMusicAddict on 2007-08-18
iceolate. Take a look at my Grip HOWTO [HERE]("http://ubuntuforums.org/showthread.php?t=183125"). Maybe I can get you using something native. ;)

---

