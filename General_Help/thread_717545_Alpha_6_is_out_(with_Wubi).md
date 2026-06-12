---
title: "Alpha 6 is out (with Wubi)"
date: 2008-03-07
forum: General Help
---

### Post by ago on 2008-03-07
Feedback welcome, as usual.

[http://www.ubuntu.com/testing/hardy/alpha6](http://www.ubuntu.com/testing/hardy/alpha6)
[http://cdimage.ubuntu.com/releases/hardy/alpha-6/](http://cdimage.ubuntu.com/releases/hardy/alpha-6/)

Notes:
* If you have troubles always try chkdsk /r from windows first
* Also try to press esc after selecting Ubuntu and give a go to the other boot options
* FAT users, note that you may have an error when upgrading kernels, that will be fixed in coming releases

---

### Post by flamelab on 2008-03-07
Everything is OK here :) with **Vista ** . Even though I like 64bit systems ( I own a core2duo laptop ) , I installed the 32bit one . I guess it is highly responsive and fast .
I have created a[ tutorial in Greece]("http://adslgr.com/forum/showthread.php?t=163942") (on the site adslgr.com on how to install Ubuntu with Wubi and I am very happy now to find out that everything is fine ! 

Great job ! Keep on !:guitar:

---

### Post by ago on 2008-03-07
64bit should also work. We forgot to remove the old caveat from the announcement.

---

### Post by lemmyc on 2008-03-08
This seemed to install OK here (using AMD64 iso), but there is a problem - on reboot, it checks the partitions - (It failed for me at this point previously, when I tried with i386 iso. Seems to work now, though I did first do a chkdsk /r as recommended.) - then I get a a dialogue box asking me to import previous settings. There is nothing suitable to import, but even if I select that option (the only one), the forward button remains greyed out. So I have to cancel the installation.
At this point I am taken to the Ubuntu desktop and all seems well.
On reboot however, I get the same import settings dialogue box and have to choose cancel again. All my saved settings and data from the previous session are lost. :(

---

### Post by lemmyc on 2008-03-08
OK, found another thread about this, and used ubiquity --automatic at the terminal to complete the installation, so that seems to be a good workaround.
My windows is XP SP3 by the way.

---

### Post by ago on 2008-03-09
This is the relevant bug [https://bugs.launchpad.net/wubi/+bug/195905](https://bugs.launchpad.net/wubi/+bug/195905) you can subscribe to know when it will be closed.

---

### Post by ago on 2008-03-13
> **lemmyc said:**
> This seemed to install OK here (using AMD64 iso), but there is a problem - on reboot, it checks the partitions - (It failed for me at this point previously, when I tried with i386 iso. Seems to work now, though I did first do a chkdsk /r as recommended.) - then I get a a dialogue box asking me to import previous settings. There is nothing suitable to import, but even if I select that option (the only one), the forward button remains greyed out. So I have to cancel the installation.
At this point I am taken to the Ubuntu desktop and all seems well.



It would help if you could provide the logs when you get shown the migration-assistant dialog.
Boot in verbose mode (press esc at the countdown after selecting ubuntu), then when you see the dialog, press Ctrl+alt+f4 and zip /var/log into the windows drive (which will be accessible as either /isodevice or /host, you'll have to check). Then attach the logs here.

---

