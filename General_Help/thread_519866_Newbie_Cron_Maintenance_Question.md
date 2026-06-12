---
title: "Newbie Cron Maintenance Question"
date: 2007-08-07
forum: General Help
---

### Post by gobbles414 on 2007-08-07
Hi Everybody,

I know that some aspect of cron runs by default nightly, weekly, and monthly, to do maintenance on Linux systems. **My question: is it possible to launch these cron scripts at will?** I'm looking for something similar to a Mac app called [onyX]("http://www.titanium.free.fr/pgs/english.html"), which at its most basic level is just a customizable launcher of cron scripts.

Thanks in advance...

---

### Post by rax_m on 2007-08-07
Yep.. you can run your scripts whenever you want.. I found this tut online:

[http://www.clickmojo.com/code/cron-tutorial.html](http://www.clickmojo.com/code/cron-tutorial.html)

---

### Post by gobbles414 on 2007-08-07
rax_m,

Thanks for the link. It was informative. **But I was actually hoping for a program with a GUI** to help me manage the cron tasks. Or alternatively, I'd like to learn when to leave my computer on so that _all_ of the cron routines run automatically.  Am I misunderstanding what cron is and what it is supposed to do? I sort of think of it as being like the disk cleanup feature in Windows -- except cron is more through obviously. As I said before, onyX for Mac OS X is the sort of app I'd like to use. *Thanks again*.

---

### Post by rax_m on 2007-08-08
Ok.. sorry I misunderstood the initial request. 

Well.. good news, is that there seems to be gui to cron called gnome-schedule
[http://www.gnomefiles.org/app.php/gnome-schedule](http://www.gnomefiles.org/app.php/gnome-schedule)

It's available in the Ubuntu universe repository (you have to enable it from System->Administration->Software sources menu item). 
Then using Synaptic, just search for gnome-schedule and you should be able to install it in one click. 

Let us know if it works how you expect.

---

### Post by gobbles414 on 2007-08-08
Okay, that's progress! Now, **how do I tell it to run all maintenance scripts?** There are no presets listed in the drop down menu.

---

### Post by rax_m on 2007-08-08
I haven't really used this so I could just be guessing.. Unfortunately the documentation on the website is non-existent :-/

1. I wouldn't use any presets
2. You have to create a task for each maintenance script you have
   OR Create a master maintenance script that runs all the scripts you need to run
   I think the first one is better as it gives you more flexibility. 
3. You don't need to worry about the advanced tab unless you want to specifiy a time of day to run. Actually, if you're running multiple scripts you might want to do this to specify some ordering. 
4. I think you'll have to either give the full path to your scripts, or add your scripts so that they are in the path. 

Bear in mind I haven't done this with this tool, or even have that much experience with Cron. I would suggest you create some non-desctructive scripts and play around with the tool and that is probably the best way to learn it.

---

### Post by gobbles414 on 2007-08-09
rax_m

I cannot thank you enough for all of your help.

Here is where I am getting confused: In Mac OS X, there are maintenance scripts built into the operating system that usually run in the "wee hours of the morning" -- around 2:00 AM I think. There are daily, weekly, and monthly scripts... all designed to keep the computer in top working order.

I have been under the impression that all Unix-based operating systems, which includes Linux obviously, contain these scripts and run them in the same manner. **Is this true?** If so, my goal right now is to be able to activate these scripts on demand in Ubuntu through a GUI.

---

### Post by rax_m on 2007-08-11
As far as i know there are no default cron jobs that are needed for system maintenance.. so I don't think you have to worry about it. 

I think there might be some things like "updatedb", but this will catchup the next time you switch on your machine. I've never heard of anyone wanting to run these manually and I think a lot of people on these forums turn their computers off. 
I personally have not had any issues on my laptop which I power off most days.

---

### Post by gobbles414 on 2007-08-12
After doing some additional research via Google, it seems like the cron maintenance scripts to which I have referred in this thread may be more a feature of FreeBSD-based operating systems.

While system performance is a small worry of mine, my biggest worry is privacy. Maybe a program like Kleansweep is worth a try?

---

### Post by tr333 on 2007-08-12
You might want to try anacron instead of cron.  Anacron is a command-scheduler like cron, but doesn't assume that the system is running continuously.  If your computer is not turned on when a cronjob is set to run, then it won't get run.  If you are using anacron then the job will be set to run the next time the computer is turned on.  Anacron jobs are specified in terms of time intervals, unlike cron which specifies jobs in the specific time of day.

FYI:  OSX now uses [launchd](http://en.wikipedia.org/wiki/Launchd) instead of cron/anacron/etc.

---

### Post by dagnabit dang doohickey on 2007-08-12
These are the commands you're looking for:
```
sudo run-parts -v /etc/cron.daily
sudo run-parts -v /etc/cron.weekly
sudo run-parts -v /etc/cron.monthly
```
But, you don't need to run them, as they will automatically be run by anacron.

If you're curious, check out the man pages for crontab and anacrontab.

---

### Post by gobbles414 on 2007-08-12
Hi all,

Well, I've learned a lot from the last couple of posts. Thank you! I'm not sure if any of the cron jobs actually did anything. Daily, weekly, and monthly took less than one minute combined. Anyway, below is the output from my cron jobs.

user@computer:~$ sudo run-parts -v /etc/cron.daily
run-parts: executing /etc/cron.daily/0anacron
run-parts: executing /etc/cron.daily/apport
run-parts: executing /etc/cron.daily/apt
run-parts: executing /etc/cron.daily/aptitude
run-parts: executing /etc/cron.daily/bsdmainutils
run-parts: executing /etc/cron.daily/chkrootkit
run-parts: executing /etc/cron.daily/logrotate
run-parts: executing /etc/cron.daily/man-db
run-parts: executing /etc/cron.daily/rkhunter
run-parts: executing /etc/cron.daily/samba
run-parts: executing /etc/cron.daily/slocate
run-parts: executing /etc/cron.daily/standard
run-parts: executing /etc/cron.daily/sysklogd
user@computer:~$ sudo run-parts -v /etc/cron.weekly
run-parts: executing /etc/cron.weekly/0anacron
run-parts: executing /etc/cron.weekly/man-db
run-parts: executing /etc/cron.weekly/popularity-contest
run-parts: executing /etc/cron.weekly/rkhunter
run-parts: executing /etc/cron.weekly/sysklogd
user@computer:~$ sudo run-parts -v /etc/cron.monthly
run-parts: executing /etc/cron.monthly/0anacron
run-parts: executing /etc/cron.monthly/scrollkeeper
run-parts: executing /etc/cron.monthly/standard

Anacron seems like it might be the method of choice for my laptop. But I would rather not go in an edit the anacrontab file until I know more about what each of the processes above is designed to do. Any additional thought and comments would be greatly appreciated.

---

### Post by dagnabit dang doohickey on 2007-08-13
There's no need to do do anything. It's already in there. ;)
Ubuntu has anacron take control of these cron tasks by default.

Take a look at /etc/crontab and /etc/anacrontab

---

### Post by gobbles414 on 2007-08-13
Hi DDD,

Thanks for posting. So what do all of those tasks do to the system anyway? Why did they take less than two minutes? And, would something like Kleansweep still be a good idea?

---

### Post by cookfromfrozen on 2007-08-17
all the default maintenance scripts do is rotate logs (i.e. archive and compress old logs in /var/log), clear out the manpage cache and do some minor stuff with apt (perhaps update packages too if you have it set to)

it also updates the slocate db, which is what takes most of the time, but it still completes quite quickly

theres nothing done that's critical for system running, and if you shut your pc down a lot, most of them never get a chance to run very often anyway.  that's why it uses anacron instead of cron, because not everyone leaves their pc on 24/7

---

### Post by gobbles414 on 2007-08-19
Hi cookfromfrozen,

Thanks for that information. Can you, or anyone else, recommend programs to help me with my privacy concerns?

---

### Post by gobbles414 on 2007-08-27
bump

---

