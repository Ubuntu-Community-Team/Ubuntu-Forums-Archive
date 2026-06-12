---
title: "long delay in GUI startup (6.06 LTS)"
date: 2007-07-03
forum: General Help
---

### Post by MrCheese on 2007-07-03
My wife rebooted my Ubuntu box (6.06LTS) while it was running some scripts converting avi to dvd (ie lots of disk access going on). The system is largely ok but is taking about 5 minutes from logging on in gdm to the desktop finally appearing. Once up, I also found the disk manager is not responding.

I'm assuming that something is corrupt. I did an e2fsck on my /home, which was all clean, and I'm not seeing anything useful in /var/log/messages, just stuff relating to .gconf xml. This problem happens for all users, inc. root.

My /home contains a lot of data but is on a seperate hdd to the rest of the system so it's not impossible to re-install if neccessary. I'd like a few pointers from anyone who may have experienced a similar problem & recovered without a reinstall though, if possible, as I have quite a lot of custom bits & pieces bolted on.

---

### Post by kfrance on 2007-07-10
I am having a similar problem.  It seemed to have happened to me when I basically filled my root partition and then tried to log in.  Even after removing the files It still takes 5 minutes to log in.  I don't have an answer yet but hopefully someone can shed some light on how to fix this problem.

---

