---
title: "Cron day-of-week number seems to be wrong"
date: 2007-09-12
forum: General Help
---

### Post by Nesman on 2007-09-12
Running Kubuntu 6.10, I set a weekly cron job to run a system backup.  I have a link to the backup script in /etc/cron.weekly and I have this line in /etc/crontab

```
47 2    * * 0   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.weekly

```

I would expect this to run Sunday morning, but it has run Wednesday since I set it up two weeks ago.  Today is 9-12 and it ran last week on 9-5.

Is my cron crazy, or does it happen this way with others as well?  I know that I could just use Sun instead of 0, but that's not the point.

The closest thing that I can think might be that it isn't counting days of the calendar week, but days since the start of the epoch.  :confused:

If my math is right, the timestamp for today should start at 1189641600, and 1189641600 mod 7 is 0.

Any thoughts?

Edit: 
It looks like the original day "0" could have been a Wednesday.  Maybe I'm not nuts.
```
cal jan 1970
    January 1970
Su Mo Tu We Th Fr Sa
             1  2  3
 4  5  6  7  8  9 10
11 12 13 14 15 16 17
18 19 20 21 22 23 24
25 26 27 28 29 30 31

```

---

### Post by pmg on 2007-09-13
The command your cron is running is a compound command.  It runs the fist command, which is "test -x /usr/sbin/anacron" and then conditionally runs the second command, that being what is after the "||".  The first command is testing to see if the file /usr/sbin/anacron exists and is executable.  If it doesn't exist or is not executable, it then runs the second command (the runs-parts.)  The idea is if **anacron** exists, **cron** lets the former handle running the scripts in the cron.weekly directory.  The idea behind anacron is that many systems now days are not always on, so it's designed to run things when the system *is* on.  It runs jobs in the cron.weekly directory that haven't been run in (at least) a week.  It keeps track of when it last ran them by touching the file /var/spool/anacron/cron.weekly.

If you really want to run a job at a specific time, and if the computer isn't on not run it at all, then you should use **cron** and put your own entry in the crontab file pointing at your script, and not use the /etc/cron.weekly directory.

You could set the timestamp on the /var/spool/anacron/cron.weekly file to make anacron think it last ran those scripts on last Sunday, and it will then run them next time it see it's been a week since they ran (be that Sunday, or the next time the computer is on after that.)

---

### Post by Nesman on 2007-09-13
Thank you!  I'm going to read the anacron man page now.  I should have caught that.

---

