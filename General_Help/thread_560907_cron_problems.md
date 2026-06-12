---
title: "cron problems"
date: 2007-09-26
forum: General Help
---

### Post by SteinbergerNate on 2007-09-26
Hello!
I've been trying to get cron to work. It's running but for some reason, the jobs in crontab don't seem to be running.

---

### Post by Dardie on 2007-09-27
Hi Nate,

you'll need to provide some more info than that. How about posting a copy of your crontab file for a start. Are you using the system-wide crontab or a personal one (with crontab -e) because I think the formats vary a little...

---

### Post by SteinbergerNate on 2007-09-27
I'm using a personal crontab. 

```
05 07 * * * gpilot-install-file --later .newsupdate/*
45 06 * * 1 avast-update
50 06 * * 1 avast
* * * * * /usr/bin/gpilot-install-file --later ~/.newsupdate/*   >/dev/null 2>&$
```

I've also tried using gnome-schedule to make sure I'm using the correct format.

---

### Post by SeanTater on 2007-09-27
You can check the cron log in /var/log, for one. But it might not be cron.. Have you tested that command in a terminal? Not do mention, does 2>&$ work? Don't you mean 2>&1

---

### Post by SteinbergerNate on 2007-09-27
Yup. I tested it in the terminal. 

oops! That last part is there it was just off the screen and so I didn't get it.

Oh, and I'm not finding a log for cron there.

---

### Post by SeanTater on 2007-09-27
Oops, cron's log is actually part of syslog. So look in /var/log/syslog


If you don't mind this being hourly, daily, weekly, or monthly, you might consider setting that in a script and putting it in one of the /etc/cron.{daily,hourly, etc} folders.

I don't have much experience with cron, but it may be in your best interest to try:

```
sudo /etc/init.d/cron restart
```

---

### Post by SteinbergerNate on 2007-09-27
Yeah, I want the commands to be mostly daily. I have that one in there every minute so that I can see if it worked or not.

---

### Post by SteinbergerNate on 2007-09-27
Ok, it looks like the commands are showing up in syslog but they're not actually being executed. Like I said before, I've tried those commands in the terminal and they work.

---

### Post by SteinbergerNate on 2007-09-27
ok. I just tried putting a script into cron.hourly and it still didn't work.

---

### Post by tszanon on 2007-09-27
Using the folder cron.daily, cron.hourly and others makes cron simple to use, but it has some requirements, like:
- scripts in those folders can't have any dot in the filename (myscript.sh is invalid, for example)
- I don't remember, but I think filenames can only have letters (A-Z), numbers and dashes. So, all my scripts are named like "backup-script-sh".

If that's the problem, just renaming the files will solve the problem.

---

### Post by SteinbergerNate on 2007-09-27
Nope. my script is named newsupdate. Not sure what the deal is.

---

### Post by 7echno7im on 2007-10-08
did anyone ever find a solution?  I am having a very similar problrm with ntpdate, I am trying to get my cron to run every minute, cron.log says it is executing, but it is not running.  If I run it manually from CLI, it works fine.  My post is here:

[http://ubuntuforums.org/showthread.php?t=570060](http://ubuntuforums.org/showthread.php?t=570060)

---

