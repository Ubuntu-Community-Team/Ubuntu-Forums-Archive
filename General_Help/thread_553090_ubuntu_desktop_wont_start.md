---
title: "ubuntu desktop wont start"
date: 2007-09-17
forum: General Help
---

### Post by billybag on 2007-09-17
i get to the loading screen and it loads a bit but then it gives me a command screen. something about a block error and i should use FSCK as root. which i do. and i get a crap load of buffer I/O error messages for device hda1

i get back to command promp where it tells me i should install apt get by using APT-GET INSTALL APT which i do and then it says something like  BASH: APT COMMAND NOT FOUND TRY USING APT-GET INSTALL APT

hahaha

i have also used GPARTED like 7 times to check the drive and it has complete all 7 times. what else can i try?

EDIT> also while in FSCK i keep havint o do force rewrites

EDIT II. Okay so i am getting that Hda1 is CLEAN now when i do FSCK again

---

### Post by reckless2k2 on 2007-09-17
have you already installed this and have been using it or you are trying to install? if you are trying to install, use the alternate disc instead of the livecd.

---

### Post by Wolki on 2007-09-17
> **billybag said:**
> i get to the loading screen and it loads a bit but then it gives me a command screen. something about a block error and i should use FSCK as root. which i do. and i get a crap load of buffer I/O error messages for device hda1

i get back to command promp where it tells me i should install apt get by using APT-GET INSTALL APT which i do and then it says something like  BASH: APT COMMAND NOT FOUND TRY USING APT-GET INSTALL APT

Apparently your root drive can't be mounted, probably a drive error. I hope you have backups of your data...

One thing you could try is starting from a live cd, then do "sudo e2fsck -cc -C 0 /dev/hda1". Maybe your hard drive just has some bad sectors.

And your system can't find apt. because it's on the root drive which you can't mount.

---

### Post by billybag on 2007-09-17
thanks. Yeah i have been using it for a couple years... it just randomly did this.
i will try the liveCD suggestion from Wolki
thanks

---

