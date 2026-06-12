---
title: "System keeps freezing with unkillable task at 100%"
date: 2014-01-03
forum: General Help
---

### Post by Digicrat on 2014-01-03
This issue has been occurring about once a week for the past few weeks now on my 27" iMac running Xubuntu 12.04 LTS with the AMD Catalyst video drivers.  I can SSH into the machine, but the GUI is completely frozen.  The first two times top showed that Firefox was consuming 100% of CPU usage, but could not be killed except by restarting the machine.  This time its the 'starwars' scrensaver.  I can execute the kill, kill -9, or killall commands without issue, but they have no apparent effect.  

Edit: top showed in each case that the task in question is in the 'R'/running state.  It is not suspended.  

I've never seen unkillable tasks in Linux before. Any ideas on what might be going on?

thanks,
- David

---

### Post by col48 on 2014-01-03
I just searched the internet using 'linux unkillable' and it seems the particular task is not very likely to be the problem.  There are many forums with this question raised in some form.  Most of what the search turns up is very 'geeky' and therefore beyond my ken but it looks like it would be worth making sure you have a good backup and checking your RAM.  Maybe someone has something more specific to add?

---

### Post by tgalati4 on 2014-01-03
Turn off your screensaver.  Some screensavers are pathological.  They completely consume your machine.  Use a black screen and be content.  Setting screensaver to random is your ticket to lockup.  

Install *htop* and watch what is going on.  You can kill tasks from there.  Start with Signal 15 (terminate) and if that doesn't work then use Signal 9 (terminate with prejudice).

*kill -9* won't work if don't use the correct process ID (PID).  Sometimes you need to kill the parent PID since more children PID's will get created in multithreaded applications.

---

