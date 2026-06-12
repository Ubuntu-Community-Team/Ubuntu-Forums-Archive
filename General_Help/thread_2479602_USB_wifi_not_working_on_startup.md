---
title: "USB wifi not working on startup"
date: 2022-09-29
forum: General Help
---

### Post by andy205 on 2022-09-29
I have Tp-link tl-wn725n.
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291075&stc=1[/IMG]
On startup it is completely dead. Green LED is not flashing. Internet is not working. I have to pull it out of USB port and put it back in in order to it start working. But all my other USB devices (keyboard, mouse) are working right away.

Is there some fix? Even some hack, like a console command that will restart that USB port instead of I have to go under table, behind PC and manually pull it out of PC on each startup of system?

---

### Post by &amp;KyT$0P# on 2022-09-30
To help troubleshoot this, maybe start by comparing output of the [wireless-info script]("https://ubuntuforums.org/showthread.php?t=370108") when your adapter is dead on startup vs after you've unplugged it & plugged it back in & it's working?

---

### Post by Tadaen_Sylvermane on 2022-10-04
I solved this in another thread. I forgot to search before posting. Here is the solution I found. Pretty sure it's the exact adapter you have as well.

[https://ubuntuforums.org/showthread.php?t=2479719](https://ubuntuforums.org/showthread.php?t=2479719)

---

