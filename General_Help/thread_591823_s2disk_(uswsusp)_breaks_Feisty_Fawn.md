---
title: "s2disk (uswsusp) breaks Feisty Fawn"
date: 2007-10-25
forum: General Help
---

### Post by pgmer6809 on 2007-10-25
2007-10-25
s2disk does not work on Feisty. (That is disk, the 'safe' one, not ram the 'risky' one.)
I tried this out on a plain vanilla DESKTOP no fancy hardware etc. just an ASUS mobo, pentium III.

It will shutdown OK, but when I try to reboot the machine it hangs during the boot process. In effect it makes my machine unusable. I did the recommended sudo dpkg-reconfigure uswsusp and answered the questions with reasonable defaults.

How to recover without re-install?
I booted from the live distro CD (any would work) and ran gparted. There I noticed that my swap partition was no longer considered to be Linux swap by gparted, but some unknown partition type.
I changed the partition type back to Linux swap and rebooted from the hard drive.
The system came up OK.

---

### Post by mbeierl on 2007-10-25
My experience with the default hibernate (store running system to disk - swsusp) had been 100% broken. - it's never worked for me.  I always use TuxOnIce instead ([www.tuxonice.net](www.tuxonice.net))

There are some nice folks who have recreated the Feisty kernel with TuxOnIce (suspend2) support built in:

[http://3v1n0.tuxfamily.org/dists/feisty/index.html](http://3v1n0.tuxfamily.org/dists/feisty/index.html)

Or you can go brave and compile your own kernel:

[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

Best of luck!

---

### Post by mbeierl on 2007-10-26
Oh, and assuming your swap partition is /dev/sda4, you could fix it this way instead:
```
mkswap /dev/sda4
```

---

### Post by minaev on 2007-10-26
s2disk worked on my Thinkpad T60 under Feisty till I installed 7.10. Did you try to disable the splash screen during the boot process to see where it get stuck?

Oh, and check your swap partition!

---

