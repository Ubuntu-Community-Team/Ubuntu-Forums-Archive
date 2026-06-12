---
title: "Automatic shutdown at 1am"
date: 2007-02-04
forum: General Help
---

### Post by MIBMIBMIB on 2007-02-04
I'm hoping this is a very simple thing to do, but I'm quite new at Ubuntu.

I've figured out that the shutdown command allows me to specify when I'd like the machine to shutdown.  What I'd like to do is make this automatic, in the sense that everytime the machine boots up it knows to shutdown at 1am.  I'm guessing that I need some kind of script that executes shutdown with the relevant parameters, executed during the bootup sequence (vaguely I'm thinking I need a bash script to be triggered in the init folder?)  Trouble is I'm not sure quite how to do this.  Could anyone help a little?

Many thanks.

---

### Post by Choad on 2007-02-04
well, i have never done this before but im sure it is done with cron

cron is the scheduleing daemon used in many linux distributions

looking through the man pages, i think you would do 

crontab -u your_user_name -e

and add something in. quite what, i dont know

---

### Post by WW on 2007-02-04
For something as drastic as shutting down the computer (for which you will need root privileges), I recommend using the system-wide crontab.  As root (i.e. with sudo or gksudo), edit the file /etc/crontab, and add this line:
>  0 1 * * * root /sbin/shutdown -h now
The first two numbers are the time (minutes first, then hour).  To test, you could put the current time (using a 24 hour clock) + 1 minute.  (But first be sure you have saved your files in any programs that are running!)

Edit: I am curious... why do you want to automatically shut down at 1 AM?  What if you are working late, and you forget about the automatic shutdown?  If you are never working late, why not just turn it off when you are done?  Or is this some sort of server?

---

### Post by Choad on 2007-02-04
> **WW said:**
> For something as drastic as shutting down the computer (for which you will need root privileges), I recommend using the system-wide crontab.  As root (i.e. with sudo or gksudo), edit the file /etc/crontab, and add this line:

The first two numbers are the time (minutes first, then hour).  To test, you could put the current time (using a 24 hour clock) + 1 minute.  (But first be sure you have saved your files in any programs that are running!)

Edit: I am curious... why do you want to automatically shut down at 1 AM?  What if you are working late, and you forget about the automatic shutdown?  If you are never working late, why not just turn it off when you are done?  Or is this some sort of server?
could make a little program that pops up a console and asks you to hit a key in 10 seconds or the system will shut down :) that would solve the "working late" issue

---

### Post by MIBMIBMIB on 2007-02-04
Choad: Thanks for the help, I was able to search for cron and found the following helpful article:

[http://www.cyberciti.biz/tips/howto-shutdown-linux-box-automatically.html](http://www.cyberciti.biz/tips/howto-shutdown-linux-box-automatically.html)

which provided roughly the same approach the WW suggested.

WW:  Thanks for the info.  You guessed right - it's basically a server.   I have set up a machine running Ubuntu - which has no monitor or keyboard - in order to run SlimServer software (which is the software for a music system called Squeezebox).  I can start the machine by pressing the power button on the Squeezebox via wake-on-LAN.  However, to shut the machine down again, I have to either start up my laptop and use a VNC connection to the SlimServer machine and shut down that way, or I have to go and find the box which is hidden away to press the power button.  If I forget to switch the box off, it'll just keep running.  If this isn't a good approach, I'm happy to try any other suggestions.  Thanks again.

---

### Post by nikhilsinha on 2007-11-16
Try GShutDown from Synaptic manager.
Then Applications ->  Accessories -> GShutDown.
It is a GUI based Automated Shutdown Utility!
See if this is useful to you..... it was exactly what I needed, to shutdown system automatically at a specified time, with GUI and Visual warnings.

---

