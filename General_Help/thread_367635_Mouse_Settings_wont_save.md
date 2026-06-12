---
title: "Mouse Settings wont save"
date: 2007-02-22
forum: General Help
---

### Post by lucas42 on 2007-02-22
Hi, my mouse (touchpad) has become quite unresponsive.  When I go into System>Preferences>Mouse, it says that its on the slowest setting - I keep changing it back to the fastest, but it dosen't remember this and the next time I go into it, its back where it started.  Is there a configuration file somewhere where I can change the mouse settings without having to use the mouse preferences?

---

### Post by DagMan on 2007-02-24
I had the opposite problem, that it was too fast and this worked.  Perhaps it will work the other way around for you.  It took a lot of trying to get the right numbers in xorg.conf [http://ubuntuforums.org/showthread.php?t=230197&highlight=touchpad+sensitivity](http://ubuntuforums.org/showthread.php?t=230197&highlight=touchpad+sensitivity)
later in the thread someone suggests simply installing a program that is supposed to do the same.  It didn't for me but it may for you.

Good luck

---

### Post by lucas42 on 2007-02-24
Thanks,  I tried this and it works great.  I edited xorg.conf and installed gsynaptics and aswell  as fixing my problem, I also got vertical scrolling working, which I hadn't got working before.              Thanks!

---

