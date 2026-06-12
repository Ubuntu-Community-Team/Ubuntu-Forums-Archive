---
title: "Turn off and on Ubuntu automatically"
date: 2008-03-22
forum: General Help
---

### Post by _sAm_ on 2008-03-22
Hi

I don't use my Ubuntu server from about 0700 in the morning to 1700. Is it possible to make it auto-shutdown and start up for that time every day. The idea is to save some power/money.

Thanks for any suggestions:-)

---

### Post by ubrox on 2008-03-22
you can do a scheduled shutdown but a startup cant be scheduled. 

Add a cron job or follow instructions here:
[http://www.ubuntugeek.com/schedule-tasks-using-gnome-schedule-a-cron-at-gui-in-ubuntu.html](http://www.ubuntugeek.com/schedule-tasks-using-gnome-schedule-a-cron-at-gui-in-ubuntu.html)

Here is the problem with automatic startup - who tells the system to turn on? Some external entity has to tell the system to wake up either physically or through an electronic signal. 

Let me know if I need to explain more.

Thanks,
Kalyan

---

### Post by _sAm_ on 2008-03-22
Off course your right - stupid question. But scheduled turn it off is more then enough, I can just turn it on when I come back home. 

*Let me know if I need to explain more.*
Not at all, thanks for the link and answer, I will give it a try:-)

---

### Post by pointone on 2008-03-22
Some routers will allow you to send wake-on-LAN signals to connected computers.

---

### Post by kaivalagi on 2008-03-22
You could choose to go into suspend mode, you can then resume based on a timer...

I don't know the specifics but I will be investigating when I put some more time into setting up my MythTV box, I need to suspend and resume by remote and for scheduled recordings. I have seen some posts on this in the past but haven't really digested the details...

So I guess the question is "would suspending and resuming be good enough?"

---

### Post by _sAm_ on 2008-03-22
*would suspending and resuming be good enough*

Yes, that would be nice,I guess sleepmode/hibernation would use a lot less power then on. So please post back if you find a solution for this:-)

---

### Post by kaivalagi on 2008-03-22
Hibernation will turn your PC off, so the only option is to suspend to memory

If you want to do some investigating you can start with these links, the first looks useful, the second could become useful (all based around media center box setup):
[http://www.mythtv.org/wiki/index.php/ACPI_Wakeup]("http://www.mythtv.org/wiki/index.php/ACPI_Wakeup")
[http://www.htpcnews.com/forums/index.php?showtopic=23148]("http://www.htpcnews.com/forums/index.php?showtopic=23148")

I can't promise I'll get anywhere with this stuff soon, so if you can have a crack at it, and post back your questions/results, you might get to a solution quicker than waiting for me to try! For a start I'll have to get my wife away from the TV before I can play around with suspend/resume :)

I think a combination of ACPI and Cron scheduling will do the job...both of which have good support material

You may also want to follow the thread linked below, looks similar :) [http://ubuntuforums.org/showthread.php?t=730544]("http://ubuntuforums.org/showthread.php?t=730544")

I'll come back with any details as and when I can...I hope that helps

Cheers

---

### Post by Son of Silas on 2008-03-31
> **kalyanakrishna said:**
> you can do a scheduled shutdown but a startup cant be scheduled. 

Add a cron job or follow instructions here:
[http://www.ubuntugeek.com/schedule-tasks-using-gnome-schedule-a-cron-at-gui-in-ubuntu.html](http://www.ubuntugeek.com/schedule-tasks-using-gnome-schedule-a-cron-at-gui-in-ubuntu.html)

Here is the problem with automatic startup - who tells the system to turn on?
Kalyan

I have the scheduled turn ON problem sorted. There's an option in my BIOS setup to start the PC at a given time and/or date, so it boots everyday at 7am no problem.

The issue I have is getting the damn PC to shut down. I installed Gnome Schedule, added a 'shutdown -h now' job to run every night, but nothing happens. I suspect it needs to be run as root, but i don't know how to do that. I have tried starting Gnome Schedule as root from a terminal, but i get an error saying 'no crontab for root'

---

