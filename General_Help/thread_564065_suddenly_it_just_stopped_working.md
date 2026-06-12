---
title: "suddenly it just stopped working"
date: 2007-09-30
forum: General Help
---

### Post by musicalmike on 2007-09-30
One time I when I tried to boot into ubuntu, the thing just hanged while initializing all the various daemons and processes that are started when booting, when I tried to restart, when I selected "wubi ubuntu" from the boot menu I was presented with the following:

booting 'find /wubi/boot/grub/menu.lst'

booting 'find /menu.lst'

find --set-root --ignore-floppies /menu.lst

error 17 file not found

press any key to continue.

I did not touch anything in the wubi folder, this happened straight out of the blue, and I need help resolving it. Thank you.

---

### Post by ago on 2007-10-01
Try to run chkdsk /r from windows cd
That might be a hal bug (some people experienced problems after installing the newer package of hal in a software update)

---

### Post by kevinmedina on 2007-10-01
I just got this error too, and it just so happens that I installed all the major upgrades with the exception to the HAL Backport updates; I've been avoiding those like the plague.  Since I didn't download any HAL updates, is there any other possibilities?

I'm going to try chkdsk when I get back from work;  I'll let you guys know what happens

---

### Post by MCMXC on 2007-10-01
Hi, i'm in the same situation...it just stops at "booting 'find /wubi/boot/grub/menu.lst'". It just stays with this and nothing happens.

I tried with "chkdsk /r" but nothing changed:(

---

### Post by nooby on 2007-10-02
> **ago said:**
> Try to run chkdsk /r from windows cd
That might be a hal bug (some people experienced problems after installing the newer package of hal in a software update)

Do you know if that is fixed with the coming WUBI for Gutsy 7.1 version. 

What would one miss if one didn't do the internal upgrade. One just ignores the prompt upgrade. Will not the latest WUBI with 7.1 have the latest upgrades?

---

### Post by ago on 2007-10-02
There are different reasons why wubi doesn't work. Don't mix them up.

1. If you hard reboot, the filesystem can get corrupted. In this case you need to run chkdsk /r
2. Hal problem: when you do an upgrade the new version does not work well for some users, you need to downgrade the hal package and then it should work
3. Grub issues. Check #1 first. Make sure that your boot files look right (boot.ini in XP and bcd in vista). Make sure that the wubi files are in place. You can press ins rapidly at the beginning of the bootloader then run the commands manually to check the error (type help).

---

### Post by musicalmike on 2007-10-02
Thanks guys, but I was able to fix it by running JkDefrag C:/wubi from windows.

---

