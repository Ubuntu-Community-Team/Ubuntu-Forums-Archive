---
title: "Any task scheduler?"
date: 2005-03-27
forum: General Help
---

### Post by core on 2005-03-27
Isn't there any nice graphical task sheduler similar to Windows'? I mean to schedule tasks to autostart / autostop at specified time, or maybe shutdown system automatically too.

Thanks in advance for any suggestions of recommendations.

---

### Post by Dromio on 2005-03-27
[QUOTE=core]Isn't there any nice graphical task sheduler similar to Windows'? I mean to schedule tasks to autostart / autostop at specified time, or maybe shutdown system automatically too.

Thanks in advance for any suggestions of recommendations.[/QUOTE]
 Linux uses cron to schedule tasks.  You can manually edit your own crontab with any text editor.  If you'd like a nice GUI for it, there is gcrontab for GTK (pretty ugly) and kcron for KDE.

---

### Post by core on 2005-03-27
Thanks. But tell me, i've installed gcrontab but i'm having some difficulties understanding how it works. I mean, the way i see it, defining something like
```
02-04 * * * * mozilla-firefox
``` 
would run firefox between minutes 2 and 4 of every hour. am i correct?
EDIT: fgot to say, i'm posting this because i wasn't able to get cron to preform it's task. using gcrontab, i've created a task, and then set the current file as the current crontab file. i even tried to save the file somewhere and then set it as default crontab file. but it still didn't work.

also, i've seen in some packages' description that cron requires the computer to be up 24/7. How so? Will the tasks be twisted after rebooting or so? Or they just meant to say "remember, if your computer is off, no tasks will be performed! (lol)"?

thanks once again.

---

### Post by PMO6022 on 2005-03-27
I find it easiest to just edit the crontab file by hand, so I've not actually used gcrontab myself, but I assume that the fields are the same.  If you want to do it manually, simply type "crontab -e" at the console.  

Anyway, here is what the fields mean:

minute   hour   dayofmonth   monthofyear   dayofweek   command

the possible values are: 
    minute (0-59),
    hour (0-23),
    day of the month (1-31),
    month of the year (1-12),
    day of the week (0-6 with 0=Sunday)

A * is a wild card.  So yes, your
```
02-04 * * * * mozilla-firefox
```
should run firefox every hour between minutes 2-4.  Try editing the crontab manually and see if it works.  I have several cron jobs set up running this way.  Good luck.

---

### Post by core on 2005-03-28
[QUOTE=PMO6022]I find it easiest to just edit the crontab file by hand, so I've not actually used gcrontab myself, but I assume that the fields are the same.  If you want to do it manually, simply type "crontab -e" at the console.  
[/QUOTE]
and so i did, but the results are the same. i even tried to reset my system clock to HH.59 just to see if it needed the hour to change to work.
neither manually nor using gcrontab, cron system does not seem to respond. does it have anything to do with permission issues?or maybe something i've installed. i remember yesterday, before i tried this, i installed something called fcron (i think) that required to remove anacron from the system. after i realized fcron was not graphical as i was looking for one, i removed it and anacron was installed back. should this be interfeering?
thanks. and sorry 'bout the boring trouble :p

---

### Post by PMO6022 on 2005-03-28
I don't know about fcron or anacron.  If the command you are trying to run requires root privliges, then you need to install it in root's crontab.  If that is the case, try sudo crontab -u root -e 

You may need to actually have a root account for this to work.  I would suggest trying to get it to run some simple command that you'll easily see is working or not first.  Sorry, this is probably not so helpful...

---

### Post by agenkin on 2005-03-28
First off, you would probably not be able to reliably run a graphical application from within a crontab: the application won't be able to connect to the X server.  I suggest that you first get a hang of using the cron scheduler with non-graphical applications.  You may need to play around with the DISPLAY environment variable and the `xhost' to allow an X-based program to be started by cron.

Secondly, the bit about the the computer needing to be on 24/7 means that if you, for instance,  schedule a job to be run at 13:00 and you turn on your computer at 13:01, the job will not be run this day.  If this is an issue, have a look a the anacron package, which does not assume that the computer is running continuously.

---

