---
title: "Cron job running"
date: 2019-10-23
forum: General Help
---

### Post by sniper8752 on 2019-10-23
I've noticed with logcheck, I've been getting e-mails every hour from the program.  I turned off the logwatch entry in the crontab file for root, but it is still running every hour.  What could I have missed?

---

### Post by TheFu on 2019-10-23
Which program? You say 2 different programs.
There are 6 places where crontasks can be. Normally, hourly, daily, weekly, monthly ... are in ....
```
$ ls /etc/cron{tab}
cron.d/       cron.hourly/  crontab       
cron.daily/   cron.monthly/ cron.weekly/ 
``` 
directories and file.

I know nothing about logcheck. Sorry.

---

