---
title: "Can't install updates without causing graphics issues/glitches. (ATI)"
date: 2013-03-06
forum: General Help
---

### Post by Cam! on 2013-03-06
Whenever I install 12.10, I'm prompted to install 280 updates. Whenever I install them and reboot, I get this glitched-up purple/orange screen which obviously prevents me from logging in and using the OS. I'm certain that this is a video driver/card issue, but how do I fix it? I have an ATI Radeon HD 6850 (1GB) graphics card. Everything seems to work fine when I don't do any updates, but I really don't want to use "vanilla", unupdated 12.10.

---

### Post by Mark Phelps on 2013-03-06
Your model ATI card supports restricted AMD drivers in 12.10.  IF you installed those through anything other than Additional Drivers, the problem is that when you do the updates, one or more of those will "break" the drivers -- as they are kernel-version-specific.

If you are using the default open-source Radeon drivers, you won't have this problem.

---

### Post by Cam! on 2013-03-06
I didn't touch ANYTHING regarding drivers. I'm looking at the Additional Drivers pane, and this is what I see: [http://i.imgur.com/nQAKRGH.png](http://i.imgur.com/nQAKRGH.png) I'm using the (what I assume to be) default, open-source drivers.

---

### Post by verymadpip on 2013-03-08
H'mmm.
I did a fresh 12.10 install this week & either drivers for my HD7770 from the repos, or some updates, broke my graphics too.
The story is much longer than that, but I feel something is amiss.
I'll be watching this for a solution.

Mark Phelps: I like you avatar, it reminds me of something from a Goya painting.

---

