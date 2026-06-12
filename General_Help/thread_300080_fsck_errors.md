---
title: "fsck errors"
date: 2006-11-15
forum: General Help
---

### Post by jeffmetal on 2006-11-15
I recently suffered a power loss to my machine while i was using it and when it rebooted i was greeted with errors on the root partition. fsck ran and terminated with the error
> fsck died with exit status 4

i followed the on screen instructions and ran fsck manually and fixed any errors but i got the error hal has not started or some variant of that when gnome started. it seems mysql is not running properly either.

what may have happened and what would be the best way to go about fixing it.

 
its a clean install of edgy so reinstalling shouldnt be too much of a problem.

---

### Post by gerkin on 2006-11-15
[http://www.ubsee](http://www.ubsee) this ost for a fix:

untuforums.org/showthread.php?t=290456&highlight=fsck+died+with+exit+status+8

---

### Post by jeffmetal on 2006-11-15
the solution for the thread you linked to [here ]("http://www.ubuntuforums.org/showthread.php?t=290456&highlight=fsck+died+with+exit+status+8")is to disable that partition in the fstab file. since this is my / partition that was borked its kinda difficult to disable it and still run ubuntu.

interestingly enough i removed a disc from my dvd-rw drive and the "failed to initialize HAL" error has stoppped on reboot.

---

