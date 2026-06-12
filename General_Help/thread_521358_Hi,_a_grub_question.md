---
title: "Hi, a grub question"
date: 2007-08-09
forum: General Help
---

### Post by Bluemotion on 2007-08-09
Hello all!
well ive happily switched over to ubuntu as my primary os,
and i also have XP installed 

i want to reinstall XP and keep it bare with only few programs because i use ubuntu for nearly all tasks. my family prefer XP.

right now i have ubuntu installed how it want it,
and xp,

when i, do reinstall Xp i assume it would mess up the Grub loader.

How do i go about this nicely, instead of ruining my bootloader and having to use the dreaded XP?:confused:
:):):) Help will be much appreiciatted

---

### Post by x1a4 on 2007-08-09
After you've reinstalled xp, boot to the Ubuntu CD and use **grub-install** to reinstall GRUB.

---

### Post by chewearn on 2007-08-09
If your GRUB resides in the MBR of the primary harddisk, XP will insist on overwriting it; you have no choice in this matter, since XP don't play nice with other OS.

However, it a simple matter to put back GRUB; see here:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub)

or here:
[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

---

### Post by Bluemotion on 2007-08-11
Thankyou Very Much for your Help :):):):)

---

