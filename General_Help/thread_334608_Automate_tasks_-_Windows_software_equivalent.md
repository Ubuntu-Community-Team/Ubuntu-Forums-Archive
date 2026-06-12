---
title: "Automate tasks - Windows software equivalent"
date: 2007-01-09
forum: General Help
---

### Post by YoungGods on 2007-01-09
Hi all,

I'm looking for a Linux equivalent for a software I use in Windows. This software allows me to schedule tasks to take place at a specific time. 
I need to do the following:
  - start an application at a given time;
  - close an application at a given time;
  - shutdown the computer;
Here's a [screenshot]("http://www.snapfiles.com/screenshots/somnifero.htm")

This is a very simple software but does exactly what I need. I'm sure there must be some kind of Linux equivalent software or even a OS feature for this. 

Any suggestions? :-k

---

### Post by 23meg on 2007-01-09
You can use cron. 

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

To shut down, you don't even need cron; ```
sudo shutdown -h 04:33
```will shut down your computer at 04:33. ```
sudo shutdown -r 13
```will reboot your computer in 13 minutes.

---

### Post by jbus on 2007-01-09
Search "schedule" in Add/Remove Applications and you find a couple of applications... Kcron for KDE and gnome-schedule for gnome.

---

### Post by YoungGods on 2007-01-09
Kcron seems to be exactly what I need. I'll give it a try as soon as I get home.
Thanks for the quick replys :)

---

### Post by cmost on 2007-01-09
Also install Anacron to ensure your scheduled tasks are executed timely, even if you shut down your system (not everyone keeps his system running 24/7.)  From Google:  Anacron is a periodic command scheduler. It executes commands at intervals specified in days. Unlike cron, it does not assume that the system is running continuously. It can therefore be used to control the execution of daily, weekly and monthly jobs (or anything with a period of n days), on systems that don't run 24 hours a day. When installed and configured properly, Anacron will make sure that the commands are run at the specified intervals as closely as machine-uptime permits.  Every time Anacron is run, it reads a configuration file that specifies the jobs Anacron controls, and their periods in days. If a job wasn't executed in the last n days, where n is the period of that job, Anacron executes it. Anacron then records the date in a special timestamp file that it keeps for each job, so it can know when to run it again. When all the executed commands terminate, Anacron exits.

I highly recommend it!  :D

---

