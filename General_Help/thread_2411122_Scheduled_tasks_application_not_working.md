---
title: "Scheduled tasks application not working"
date: 2019-01-25
forum: General Help
---

### Post by jek1 on 2019-01-25
Ubuntu 14.04 LTS

Scheduled tasks application simply does not work. I have tried it on more than one computer now, and it simply does not run any task I try to schedule. I have tried every trick I could find on this and other forums to make it work, with absolute no success. However it does apparently work for other users. What do I have to do to make it work?  Please try to explain as simple as possible to me as I am not proficient with all the heavy terminology.

---

### Post by TheFu on 2019-01-25
I cannot help with this specific application.  I've never used a GUI to schedule any tasks on any Unix-like OS.

But anacron and cron definitely work, if you'd like help with those.  [http://www.unixgeeks.org/security/newbie/unix/cron-1.html](http://www.unixgeeks.org/security/newbie/unix/cron-1.html) is pure text, explanation.

I add the following comments to all my crontabs (run **crontab -e** ), so it is clear which field means what:

```
# .---------------- minute (0 - 59)
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ...
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7)  OR sun,mon,tue,wed,thu,fri,sat
# |  |  |  |  |
# *  *  *  *  *  command to be executed
# *  *  *  *  *  command --arg1 --arg2 file1 file2 2>&1
```

Cron will not work with GUI programs. It is for batch processing at a specific time.

---

### Post by jek1 on 2019-01-28
Thanks for your answer TheFu. I went to the link you posted, but got stuck in the second paragraph (_**How to start Cron**_) already. I opened a terminal and type the command "cog@pingu $ ps aux | grep crond", but get tee response "cog@pingu: command not found".

---

### Post by HermanAB on 2019-01-28
Err... Up to the $ is a prompt - don't type it.  The command is after the dollar.

Cron should be running by default already.

---

### Post by jek1 on 2019-01-28
Thanks Herman. Okay. I have now typed "ps aux | grep crond" and get the response "jek       3614  0.0  0.0  18012  2288 pts/0    S+   17:18   0:00 grep --color=auto crond". Does this mean cron is running or not?

I have also run crontab -e and added the line "* * * * * gnome-terminal -x /home/jek/Temp/Test". Nothing happens! "Test" just displays "Test Run" and then waits for the Enter key to be pressed. It does work when run from a terminal, but does not run as scheduled (every minute as I understand it). I have tried crontab -e also on another computer and it does not run as scheduled on that computer either. What am I still doing wrong?

---

### Post by jwn-2 on 2019-01-29
I have also been using Ubuntu 14.04 for some years now, and I assure you neither gnome-schedule nor crontab -e nor adding lines to etc/crontab has ever worked. No tasks scheduled in any way do ever run. Not even adding the task to etc/cron.daily/, -hourly/, etc works. By now I have given up trying to schedule tasks.

By the way in my version of Ubuntu the daemon’s name seems to be just “cron”, not “crond” and cron is definitely running, but not scheduling anything.

---

### Post by The Cog on 2019-01-29
> **jek1 said:**
> Thanks Herman. Okay. I have now typed "ps aux | grep crond" and get the response "jek       3614  0.0  0.0  18012  2288 pts/0    S+   17:18   0:00 grep --color=auto crond". Does this mean cron is running or not?
No. That tells you that "grep --color=auto crond" is running. That is your command searching for "crond".> 
I have also run crontab -e and added the line "* * * * * gnome-terminal -x /home/jek/Temp/Test". Nothing happens! "Test" just displays "Test Run" and then waits for the Enter key to be pressed. It does work when run from a terminal, but does not run as scheduled (every minute as I understand it). I have tried crontab -e also on another computer and it does not run as scheduled on that computer either. What am I still doing wrong?
That won't work for several reasons:
* there is no path for gnome-terminal specified. It doesn't know where to find the executable. cron always needs full paths
* there is no DISPLAY specified. gnome-terminal won't know where to display its window, even if you are logged in. As a rule, it's not a good idea to try to schedule graphical applications.
* as far as I can tell, graphical apps won't run unless the relevant user is logged in, even if you set the DISPLAY variable. I have not tried to figure out why not. Ownership of the display maybe.

You could try:
```
* * * * * DISPLAY=:0 /usr/bin/gnome-terminal -x /home/jek/Temp/Test
```
P.S. It's cron that runs, not crond. Searching for crond with grep will only ever show grep running.

---

### Post by jek1 on 2019-01-29
Thanks The Cog. I have retyped the line now exactly as you suggested, but still nothing happens. I have also checked now if cron is running (not crond) and yes it is running.

---

### Post by TheFu on 2019-01-29
I've been using 14.04 for a while now.  I can assure everyone that cron works under it.  That is how daily, versioned, scheduled backups work here, among other needs.  Our backup server runs 14.04 for a few more weeks.

Putting any GUI app into cron is a really bad idea.  If you want something to test that cron is working, just append the current time to a file in /tmp/ .

cron has a few best practices which aren't intuitively obvious for people new to Unix and cron.  There are a few posts about those in these forums.  [https://ubuntuforums.org/showthread.php?t=2398585&highlight=crontab+-e](https://ubuntuforums.org/showthread.php?t=2398585&highlight=crontab+-e) is one with some links to a few scripting and cron articles that I wrote.

---

### Post by jek1 on 2019-01-29
I do not have any GUI's in my test cron. It is just a simple script displaying the words "Test Run" and then wait for the Enter key to be pressed.

---

### Post by The Cog on 2019-01-29
> **jek1 said:**
> I do not have any GUI's in my test cron. It is just a simple script displaying the words "Test Run" and then wait for the Enter key to be pressed.

But it's trying to run gnome-terminal. That's a GUI program that needs lots of setup, which is why as a minimum it needs a DISPLAY (I don't know what else, maybe lots of dependencies on its environment). I have been able to launch xeyes from cron simply by specifying DISPLAY=:0, just to prove to myself it's possible. 

But I agree with TheFu - don't try to run GUI stuff from cron. cron is for unattended tasks (i.e. no user logged in, no desktop to draw on).

P.S. You can get a better feel for this by trying to run programs from a console login, Ctrl-Alt-F1. For instance, trying to launch xeyes gets the error "Can't open display"

---

### Post by jek1 on 2019-01-29
So what should I then use to run something that needs to display some feedback to me at a certain time, e.g. a simple reminder to do something at a certain time?

---

### Post by TheFu on 2019-01-29
Maybe **plan** 
or a calendar entry in your favorite calendar tool. I use the **lightning** extension with **Thunderbird** tied into our **Zimbra** email/calendar/contacts server 
or use an alarm applet? **alarm-clock-applet** is one that I use for reminders "today."

plan is really old - from the mid-1990s. I used it for a few years.

I bet there is a way to send a notification to your DE too. You know, those annoying popup bubbles?  I don't use DEs mainly because of those bubbles, but I don't want the bloat.

---

### Post by jek1 on 2019-01-30
Okay, a reminder to do something was a bad example, I know I can use a calendar for that. But I do have scripts that need to be run at a certain time every day, and they do need some interface with me. What should I use to schedule them to run automatically? At the moment my only option is a reminder on my phone to start the scripts manually.

---

