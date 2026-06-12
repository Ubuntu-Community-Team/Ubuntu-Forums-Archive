---
title: "CRON: What it does every hour"
date: 2007-08-01
forum: General Help
---

### Post by oldcpu on 2007-08-01
Looking at my /var/log/auth.log, I see that CRON opens and closes a session every hour.

Just what exactly does this do?  And what would the consequence be if I stopped CRON?  Is it even important that CRON does this?

It is cluttering the log with all these hourly sessions.  So I was wondering what it exactly does.

---

### Post by 505 on 2007-08-01
Cron is a program that runs other programs at a certain time interval. Look at the /etc/cron.*/ directories to see which scipts are run, and when.
I do not recommand to kill cron, since other usefull processes are run by cron, e.g. checking for updates. It you want to run less scripts every hour, see what scripts are in /etc/cron.hourly, see what they do, then decide if you want to delete these, or move them to /etc/cron.daily for example.

---

### Post by oldcpu on 2007-08-02
There is nothing in cron.hourly.  But auth.log tells me that CRON is running a session every hour.

What is going on?

---

### Post by mannheim on 2007-08-02
Every hour, cron checks to see what scripts are in /etc/cron.hourly, and it runs any scripts in there. Even if there are no scripts in there, cron still looks there every hour. The line in /etc/crontab that makes this happen is (details may vary):

```

17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly

```

I wouldn't worry about it. The entries in your log file just tell you that cron is doing this task.

---

### Post by oldcpu on 2007-08-03
Is it okay to comment the above code?  Because I do not want my auth.log being cluttered with useless information.

---

### Post by AlucardZero on 2007-08-03
I don't think you should worry so much about harmless log messages.  You could disable cron.hourly by doing that, but what happens when, a few months down the road, some program need sit, and it doesn't work, and you have forgotton what you did?  I wouldn't mess with it.

---

