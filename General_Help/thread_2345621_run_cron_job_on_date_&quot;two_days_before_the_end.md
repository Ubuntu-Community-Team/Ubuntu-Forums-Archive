---
title: "run cron job on date &quot;two days before the end of the month&quot;"
date: 2016-12-06
forum: General Help
---

### Post by marchello_lippi2 on 2016-12-06
Hi all, 
How do I run cron job on date "two days before the end of the month" ? 
Thanks ahead.

---

### Post by TheFu on 2016-12-06
I would run it once daily on the 26th-29th days of every month. Then calulate the date 3 days from that date - if that is the 1st of the next month, then run the rest of the job. If any other answer, don't run anything further.

There is probably a smarter answer on the internet. I didn't search, but there are lots of how-tos for crontabs that need to be run on the last Friday of the month and other situations like that.

[https://serverfault.com/questions/661423/how-to-schedule-a-cron-job-for-the-second-to-the-last-day-of-each-month](https://serverfault.com/questions/661423/how-to-schedule-a-cron-job-for-the-second-to-the-last-day-of-each-month) says:
```
0 23 27-30 * * [ $(date +\%d -d "2 days") == 01 ] && /where/is/my/script
```

---

### Post by ian-weisser on 2016-12-06
Is the system always-on? If it may be suspended or hibernated or off, that makes the process more complex.

One solution: Add script in cron.monthly that calculates the date and creates an ['at' job]("http://www.computerhope.com/unix/uat.htm"),

Another solution: Add script in cron.monthly that sets a [systemd timer]("http://manpages.ubuntu.com/manpages/wily/man5/systemd.timer.5.html") to do the job.

---

