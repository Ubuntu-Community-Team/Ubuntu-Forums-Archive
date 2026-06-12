---
title: "libnotify 0.4.4 and notification daemon 0.3.7"
date: 2007-06-18
forum: General Help
---

### Post by Aetherius on 2007-06-18
ok, i medically need these packages. However. I can't install them from galago's source, the notification-daemon just won't compile a load of nonsense errors in the code itself. (i can't see this as actually being the case) Obviously the gutsy debs are of no use to me (tho i did try, depends on libc6 which conflicts with current tzdata ). So i just want to scream at all of you for help.

Is there any hope of me getting theses packages without totally blackballing my box or will i have to go gutsy?


(come to think of it I can't go gutsy on my lap :( )

Aeth

---

### Post by zanglang on 2007-06-18
Why not download the Feisty debs, or compile the source from the repositories using dpkg-buildpackage?

---

### Post by Aetherius on 2007-06-18
the repos versions are 0.4.3 and 0.3.6, not what i want ;)

---

### Post by zanglang on 2007-06-18
Oops, I apologize, forgot to check first! ;)
How about downloading gutsy's source, and then compiling with dpkg-buildpackage? You might have to tweak the debian control files and dependencies a bit to use feisty's versions.
[http://packages.ubuntu.com/gutsy/libs/libnotify1](http://packages.ubuntu.com/gutsy/libs/libnotify1)
[http://packages.ubuntu.com/gutsy/x11/notification-daemon](http://packages.ubuntu.com/gutsy/x11/notification-daemon)

---

