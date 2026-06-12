---
title: "Firefox segfaults on about a third of all sites containing flash"
date: 2008-06-09
forum: General Help
---

### Post by eZtaR on 2008-06-09
Hello :)

My problem is that firefox segfaults on about a third of all sites containing flash.
Before the sefault i get a lot of repititions of this error:
```
(firefox:869): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
```

and my flash is at v9.0 r124.

I've found [this thread](http://ubuntuforums.org/showthread.php?t=156138) which may be my solution. I just haven't found the aforementioned tahoma fonts.

Oh and it also crashes when i run firefox as root :S

---

### Post by ts2000 on 2008-06-09
I had problems with firefox completely freezing on Hardy Heron.  I deleted the version 3 package and reverted to Firefox-2.0 package and it works fine now with youtube.  

Good luck.

---

### Post by eZtaR on 2008-06-09
> **ts2000 said:**
> I had problems with firefox completely freezing on Hardy Heron.  I deleted the version 3 package and reverted to Firefox-2.0 package and it works fine now with youtube.  

Good luck.

I've tried with firefox-2 aswell but it doesn't help :(

---

### Post by adityakavoor on 2008-06-09
try flash 10. [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_051508.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_051508.tar.gz)

---

### Post by xebian on 2008-06-09
> **eZtaR said:**
> I've tried with firefox-2 aswell but it doesn't help :(

Well, if it's still a problem with a diff versions or combinations, then there maybe a hardware/memory issue?  Can you try the RC2 Swiftweasel with flash 9 and flash 10 beta ?

---

### Post by NilsE on 2008-06-09
Try removing libflashsupport if it is installed. You may possibly lose sound in FF but it can always be reinstalled. If you do lose sound try switching from pulse audio to alsa.

---

