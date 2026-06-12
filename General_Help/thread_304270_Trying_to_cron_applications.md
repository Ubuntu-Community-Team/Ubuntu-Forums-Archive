---
title: "Trying to cron applications"
date: 2006-11-21
forum: General Help
---

### Post by jc87 on 2006-11-21
I´m trying to use **cron** at **edgy** so i can start applications at a pre-determined date, unfortunately i´m frustrated with the following problems i keep getting into:

- Both kcron and gnome-schedule fail at starting the required actions, i set them up but nothing happens.

- I searched a while (both google and ubuntuforums) about messing with cron manually, and as an experiment i added to my crontab: 

```
20 20 21 11 2 jc87 /usr/bin/gimp 
```

to see if i could start gimp at 20:20 day 21 etc... anyway still nothing, even if i do an *sudo /etc/init.d/cron restart *

My current /etc/crontab is :

```
# This file also has a username field, that none of the other crontabs do.
SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
# m h dom mon dow user	command
17 * * * *	root	run-parts --report /etc/cron.hourly
# 
25 6 * * *	root	test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily
# 
47 6 * * 7	root	test -x /usr/sbin/anacron || run-parts --report /etc/cron.weekly
# 
52 6 1 * *	root	test -x /usr/sbin/anacron || run-parts --report /etc/cron.monthly
# This file was written by KCron. Copyright (c) 1999, Gary Meyer
# Although KCron supports most crontab formats, use care when editing.
# Note: Lines beginning with "#\" indicates a disabled task.

20 20 21 11 2 jc87 /usr/bin/gimp 
```


My  ps aux | grep cron  output is:

```
root     17429  0.0  0.1   2200   876 ?        Ss   20:18   0:00 /usr/sbin/cron
jc87     17544  0.0  0.1   2812   760 pts/0    R+   20:21   0:00 grep cron

```

Can anyone give me any tips of what i may possibly be doing wrong? Is there any other config file i need to post to give more information on the subject?

---

