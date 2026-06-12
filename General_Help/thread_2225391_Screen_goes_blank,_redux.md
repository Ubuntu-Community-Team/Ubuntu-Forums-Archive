---
title: "Screen goes blank, redux"
date: 2014-05-21
forum: General Help
---

### Post by lou6 on 2014-05-21
There is already a thread on this (marked solved) here [http://ubuntuforums.org/showthread.php?t=1325308](http://ubuntuforums.org/showthread.php?t=1325308) but it raises more questions for me.

Since there is no longer a xorg.conf file, where is "xset q" getting its data? On my Trusty install the monitor settings do indeed show that x is timing out and blanking my monitor after 10 minutes but where is the place to apply the fix shown in the solution?

Help, please...

EDIT: I tried adding "xset s 0 0" to /etc/rc.local and making the file executable but no joy...

further EDIT: apparently rc.local runs before x is started (which would explain why I not succeeding).

conclusion: added the command to .profile - works fine - marking this solved.

---

