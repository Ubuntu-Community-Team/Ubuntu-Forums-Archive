---
title: "Gutsy.Crashed. is nvidia to blame ?"
date: 2008-01-11
forum: General Help
---

### Post by jerrykenny on 2008-01-11
Just had the worst crash I've ever seen on my HP laptop.

Been scratching around the latest posts, and nvidia.firefox, and flash seem to be all under suspicion.

I did have pidgin running in the background, but i was also watching a youtube at the time. . . . . 

But i more strongly suspect nvidia for 2 reasons

  1/  This was a complete CRASH, i logged into a terminal, with ctrl-alt-f1, but even the terminal was locked !         (cpufan was going mental all the while)

  2/  I've lately been using "nvidia-settings" to dim my lcd display, as the lcd-brightness applet doesnt have any sensible kind of response with my display.

Bit of a coincidence. . . . . . 

To my reasoning, number 1 above strongly suggests a kernel problem ? rather than gnome-firefox-pidgin-flash problem. . . . . hence my disdain for nvidia  . . . . omygod !  its tainted my kernel !     scream:(

---

### Post by kellemes on 2008-01-11
/var/log shows a hole lot of logfiles to study :popcorn:

---

### Post by jerrykenny on 2008-01-11
Hi Kelemes,,, yes, I'll get round to reading them, . . . . . 

anyway ran firefox again from terminal, and accessed another youtube (try to replicate original fault)

Sam again, cpu went to max, fan goes mental, and i killed firefox promptly.

Last error message is

** (<unknown>:6436): DEBUG: no missing plugins found

but what gives?  even if firefox couldnt find a plubin, surely it would just report as-such, and not hang my system.

Now i'm not so convinced it is nvidia . . . . 

hmmmmmm

---

### Post by kellemes on 2008-01-11
Have you tried remove all plugins from Firefox to see what happens? Just install them one by one.. plugins are not always written very well..
Also, some are having these kind of issues with the Flash-plugin, maybe something to investigate?

---

