---
title: "Metacity not on startup"
date: 2008-06-09
forum: General Help
---

### Post by jeamer on 2008-06-09
Hi, clean install of 7.10, Hardy gave me problems. Got rid of compiz, now I can´t get metacity on startup. Adding ¨metacity¨ to sessions didn´t help either. Thanks.

---

### Post by tom66 on 2008-06-09
Can you run Metacity from the command line? Make sure you've added '--replace' to the command.

---

### Post by jeamer on 2008-06-09
Yup. Although why do I add --replace... both metacity and metacity --replace start up metacity for me.

---

### Post by jeamer on 2008-06-09
cool. Added metacity --replace as a startup in sessions, and now boot won't go any further than the login screen. Another awesome effect is everytime I try to login to Ubuntu on my desktop, it buggers the network I have setup through it, rendering my laptops toast. Had to login to windows for the first time in 2+ years! Unfortunate amount of trouble with the latest distros. I will do *another* clean install and go from there. Anyone else have any ideas on how to add metacity to the startup?

---

### Post by tom66 on 2008-06-09
--replace forces it by quitting the current window manager, if any, and starting Metacity.

---

### Post by jeamer on 2008-06-09
bump - 

still no metacity on startup, I re-installed gutsy again and am not going to try anything until someone knows a fix! Thanks!

UPDATE: bizarre... bizarre. So I now have metacity on startup, sortof. Added /usr/bin/metacity to sessions and the weirdest thing. Metacity launches ~ 2 minutes after boot is complete (i.e. after the HD stops spinning). I can navigate around in x with the super basic window management included with gnome, then 2 minutes later Metacity launches. Anyone?

---

