---
title: "MAIL (mailed 1 byte of output; but got status 0x004e error with crontab"
date: 2016-10-26
forum: General Help
---

### Post by NotQuiteSU on 2016-10-26
I have a cronjob that usually works.

But for whatever reason it stops, and when I check syslog, I see

> Oct 26 08:00:01 HOSTNAME CRON[24355]: (sysadmin) CMD (/home/sysadmin/scripts/websearch_v2.sh 2>&1 >> /home/sysadmin/errors.txt)
Oct 26 08:00:01 HOSTNAME CRON[24353]: (sysadmin) MAIL (mailed 1 byte of output; but got status 0x004e, #012)

/home/sysadmin/errors.txt is empty.

I am using MSMTP as an email relay with gmail. When I run /home/sysadmin/scripts/websearch_v2.sh manually, or restart crontab/reboot, everything is fine for a while. (I'm still troubleshooting that)

My Crontab:
> MAILTO=MyEMailAccount@gmail.com
# m h  dom mon dow   command
0 * * * * /home/sysadmin/scripts/redditsearch_v2.sh 2>&1 >> /home/sysadmin/errors.txt

Any ideas to what is going on with my MAIL error?

---

