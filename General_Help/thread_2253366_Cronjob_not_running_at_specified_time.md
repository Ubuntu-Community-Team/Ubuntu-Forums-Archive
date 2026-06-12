---
title: "Cronjob not running at specified time"
date: 2014-11-19
forum: General Help
---

### Post by rbishop on 2014-11-19
Hello again forum folks.  I am having an odd problem with one of my newly created servers.  I did a base install of the OS (14.04.1 server) and added my personal backup scripts to the server.  I then set the scripts to run at 2 and 3am every morning.  I then noticed my time was not correct on the server so I ran the command 
```
dpkg-reconfigure tzdata
```
and set my appropriate time zone.  I rebooted my server, to be on the safe side since it was not in production at the time.  I checked the time using the 
```
date
```
command and verified the time and date were now correct.

However my script doesn't run at the appropriate time.  I setup a demo script to run at different intervals throughout the day and none of them run at the specified time.

Any ideas on what could be happening or how I can correct it.

---

### Post by yancek on 2014-11-19
Post the entry you have for cron, nobody will be able to tell you if something is wrong with it if we don't know what it is.  Does the script run from a terminal?

---

### Post by rbishop on 2014-11-19
From my Crontab

```

0 3 * * * /scripts/daily-backup.sh

```

I am able to run the script manually with no problem.  I also see that it gets ran 5 hours after they are supposed to.  I have removed this entry from Crontab, saved, rebooted the machine, and then re-added to Crontab.  However this has not had an impact on the running of the script.

Here is the output of my log file that is created with this script showing the time and date of the script starting and ending.

```

Backup Script Started @: Mon Nov 17 08:00:01 EST 2014
Backup Script Ended @: Mon Nov 17 08:01:12 EST 2014

```

---

### Post by matt_symes on 2014-11-19
Hi

I your first post you say the time was out. Was it out by 5 hours ?

Kind regards

---

### Post by rbishop on 2014-11-19
To be honest I don't remember if the time was off by that much.  I would like to think that is what it is, but wouldn't my crontab have updated when I updated the time and rebooted the server?

---

### Post by ian-weisser on 2014-11-19
> **rbishop said:**
> wouldn't my crontab have updated when I updated the time and rebooted the server?

You crontab file wouldn't change at all.

Cron itself doesn't notice if you change time or sleep or reboot. All it does, once each minute,is to compare the system time to the job times. If it matches, cron triggers the job.

If you are running anacron, it might have run those jobs. Anacron runs a few minutes after boot, and looks for cron jobs in /etc/anacrontab that have not run.

---

### Post by rbishop on 2014-11-19
Okay so if Cron it only looking at the file for times, shouldn't it run at the correct time?  or does it have a separate time it is reading from?  

My apologies for the "noobieness" of my questions.  I am just not understanding it as I should.

---

### Post by matt_symes on 2014-11-19
Hi

Had a longer reply typed for you but this site keeps logging me out when I use my phone to access it.

This is making it almost unusable for me so here's the abridged version.

utc vs local time ? Which is set on server ?

You 5 hours different from UTC at the moment ?

```
sudo hwclock
```

post back above on server.

ntp problem ?

Kind regards

---

### Post by rbishop on 2014-11-20
Not sure what has happened, but I had to do a reboot after an upgrade...and now it seems to be working on time....<insert cheesy eerie music here>.  

Thanks for all the help and thoughts.

---

