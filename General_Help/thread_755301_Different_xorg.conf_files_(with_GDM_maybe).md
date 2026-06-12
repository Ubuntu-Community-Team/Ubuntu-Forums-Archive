---
title: "Different xorg.conf files (with GDM maybe?)"
date: 2008-04-14
forum: General Help
---

### Post by Corey on 2008-04-14
I have 2 8600gt cards. I got the 2nd one so I could hook up a 3rd monitor. When I built this machine initially though, i made sure it was future ready for SLI. That way if ever I got a 2nd card I could hook it up as SLI. Now that I've got 2 cards I set up SLI and I do see a significant boost in framerate on most games. The problem is when i'm in SLI mode I can't use multiple monitors, which is the primary reason I got the 2nd card. So now I have 2 xorg.conf files. 1 for xinerama and 1 for SLI gaming. Is it possible to setup some sort of GUI (preferably from GDM) to switch the xorg.conf files whenever I need to switch. As it is now, I have to cp xorg.conf.sli xorg.conf from a terminal and the reboot Xorg. Not the most elegant solution. I doubt GDM can handle this because it runs in X, but still it would be prefered.

Thanks in advance,
Corey

---

### Post by bodhi.zazen on 2008-04-14
See this thread :

[http://ubuntuforums.org/showthread.php?t=240150](http://ubuntuforums.org/showthread.php?t=240150)

It is written for multiple window managers, but goes over how to do this and you should be able to adapt it easily.

---

