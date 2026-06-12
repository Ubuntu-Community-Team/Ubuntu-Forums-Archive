---
title: "ati fglrx dapper upgrade composite login kick back fix"
date: 2006-10-26
forum: General Help
---

### Post by mjziegle on 2006-10-26
I'm coming from dapper so when I upgraded gnome appeared broken. Specifically it was the DRI portion of the ati (fglrx) driver. I kept getting kicked back to the login screen after the upgrade.

To fix: After upgrading make sure to add

Section "Extensions"
  Option "Composite" "0"
EndSection

to the end of xorg.conf and then run

sudo aticonfig --overlay-type=Xv

Fixed my problems. Should fix the getting kicked back out problem.

---

### Post by llamakc on 2006-10-26
Thanks for posting this. I'm certain there'll be ALOT of posts with this problem here shortly.

---

### Post by Rackerz on 2006-10-26
You get fglrx working with the latest version of Xorg and DRI enabled you know ;).

> [http://www.ubuntuforums.org/showthread.php?t=273934](http://www.ubuntuforums.org/showthread.php?t=273934)

---

### Post by mjziegle on 2006-10-27
That thread doesn't address the problem.  In edgy composite rendering is enabled by default which isn't supported by the fglrx driver so you manually have to disable it in xorg.conf as I show above.  This has nothing to do with the source of the drivers or a corrupted installation.  It applies to all versions of the driver.  I would highly recommend sticking with the packages rather than blacklisting and compiling your own driver.

Other users report the compositing issue in that thread, but a user won't be able to find that info in a regular search - hence why I created this thread.

Thanks for the heads up.

> **Rackerz said:**
> You get fglrx working with the latest version of Xorg and DRI enabled you know ;).

---

