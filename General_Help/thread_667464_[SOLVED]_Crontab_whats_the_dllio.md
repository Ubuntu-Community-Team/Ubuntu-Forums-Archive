---
title: "[SOLVED] Crontab whats the dllio?"
date: 2008-01-14
forum: General Help
---

### Post by kambrik on 2008-01-14
This is my current crontab config:

# m h  dom mon dow   command
* 2,6,10,14,18,22 * * * /usr/local/sbin/rlogr/scrptr.sh
* 1,3,5,7,9,11,13,15,17,19,21,23 * * * /usr/local/sbin/phsal/crnsc.sh
30 * * * * /usr/local/sbin/tnlwatch/crntnl.sh

It was this:
# m h  dom mon dow   command
* */4 * * * /usr/local/sbin/rlogr/scrptr.sh
* */2 * * * /usr/local/sbin/phsal/crnsc.sh
30 * * * * /usr/local/sbin/tnlwatch/crntnl.sh

My question is why are there so many log entries in the /var/log/syslog file pertaining to the cron jobs? For example every minute it looks to me that it is checking or trying to run the job or something i'm not for sure what the log is stating.  If someone could shed some light on why its logging all this it would be great.

Sample from /var/log/syslog:

2008-01-14T00:17:01-06:00 Ububox /USR/SBIN/CRON[4708]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
2008-01-14T00:30:01-06:00 Ububox /USR/SBIN/CRON[4713]: (root) CMD (/usr/local/sbin/tnlwatch/crntnl.sh)
2008-01-14T01:00:01-06:00 Ububox /USR/SBIN/CRON[4722]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)
2008-01-14T01:01:01-06:00 Ububox /USR/SBIN/CRON[4733]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)
2008-01-14T01:02:01-06:00 Ububox /USR/SBIN/CRON[4744]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)
2008-01-14T01:03:01-06:00 Ububox /USR/SBIN/CRON[4755]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)
2008-01-14T01:04:01-06:00 Ububox /USR/SBIN/CRON[4766]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)
2008-01-14T01:05:01-06:00 Ububox /USR/SBIN/CRON[4777]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)
2008-01-14T01:06:01-06:00 Ububox /USR/SBIN/CRON[4788]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)
2008-01-14T01:07:01-06:00 Ububox /USR/SBIN/CRON[4799]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)
2008-01-14T01:08:01-06:00 Ububox /USR/SBIN/CRON[4810]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)
2008-01-14T01:09:01-06:00 Ububox /USR/SBIN/CRON[4821]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)
2008-01-14T01:10:01-06:00 Ububox /USR/SBIN/CRON[4832]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)
2008-01-14T01:11:01-06:00 Ububox /USR/SBIN/CRON[4843]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)
2008-01-14T01:12:01-06:00 Ububox /USR/SBIN/CRON[4854]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)
2008-01-14T01:13:01-06:00 Ububox /USR/SBIN/CRON[4865]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)
2008-01-14T01:14:01-06:00 Ububox /USR/SBIN/CRON[4876]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)
2008-01-14T01:15:01-06:00 Ububox /USR/SBIN/CRON[4887]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)
2008-01-14T01:16:01-06:00 Ububox /USR/SBIN/CRON[4898]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)
2008-01-14T01:17:01-06:00 Ububox /USR/SBIN/CRON[4909]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
2008-01-14T01:17:01-06:00 Ububox /USR/SBIN/CRON[4911]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)
2008-01-14T01:18:01-06:00 Ububox /USR/SBIN/CRON[4923]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)
2008-01-14T01:19:01-06:00 Ububox /USR/SBIN/CRON[4935]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)
2008-01-14T01:20:01-06:00 Ububox /USR/SBIN/CRON[4946]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)
2008-01-14T01:21:01-06:00 Ububox /USR/SBIN/CRON[4957]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)
2008-01-14T01:22:01-06:00 Ububox /USR/SBIN/CRON[4968]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)
2008-01-14T01:23:01-06:00 Ububox /USR/SBIN/CRON[4979]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)
2008-01-14T01:24:01-06:00 Ububox /USR/SBIN/CRON[4990]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)
2008-01-14T01:25:01-06:00 Ububox /USR/SBIN/CRON[5001]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)
2008-01-14T01:26:01-06:00 Ububox /USR/SBIN/CRON[5012]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)
2008-01-14T01:27:01-06:00 Ububox /USR/SBIN/CRON[5023]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)
2008-01-14T01:28:01-06:00 Ububox /USR/SBIN/CRON[5034]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)
2008-01-14T01:29:01-06:00 Ububox /USR/SBIN/CRON[5045]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)
2008-01-14T01:30:01-06:00 Ububox /USR/SBIN/CRON[5056]: (root) CMD (/usr/local/sbin/tnlwatch/crntnl.sh)
2008-01-14T01:30:01-06:00 Ububox /USR/SBIN/CRON[5058]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)
2008-01-14T01:31:01-06:00 Ububox /USR/SBIN/CRON[5072]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)
2008-01-14T01:32:01-06:00 Ububox /USR/SBIN/CRON[5085]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)
2008-01-14T01:33:01-06:00 Ububox /USR/SBIN/CRON[5096]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)
2008-01-14T01:34:01-06:00 Ububox /USR/SBIN/CRON[5107]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)
2008-01-14T01:35:01-06:00 Ububox /USR/SBIN/CRON[5118]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)
2008-01-14T01:36:01-06:00 Ububox /USR/SBIN/CRON[5129]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)
2008-01-14T01:37:01-06:00 Ububox /USR/SBIN/CRON[5140]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)
2008-01-14T01:38:01-06:00 Ububox /USR/SBIN/CRON[5151]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)
2008-01-14T01:39:01-06:00 Ububox /USR/SBIN/CRON[5162]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)

Thank you

---

### Post by benblout on 2008-01-14
I think it is doing what you asked it to.
```
* 1,3,5,7,9,11,13,15,17,19,21,23 * * * /usr/local/sbin/phsal/crnsc.sh
```
Says to run crnsc.sh any minute (* in the first column) of hours 1,3,5, etc.

So that is exactly what is happening!

Does that make sense?

-Ben

---

### Post by kambrik on 2008-01-15
Ic.... That does make sense.  Ok so what would the correct way of making it run just once for those hours? Or is that what you are saying it is doing?

---

### Post by benblout on 2008-01-15
> **kambrik said:**
> Ic.... That does make sense.  Ok so what would the correct way of making it run just once for those hours? Or is that what you are saying it is doing?

When I look at this section of your log:
```
2008-01-14T00:30:01-06:00 Ububox /USR/SBIN/CRON[4713]: (root) CMD
(/usr/local/sbin/tnlwatch/crntnl.sh)
2008-01-14T01:00:01-06:00 Ububox /USR/SBIN/CRON[4722]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)
2008-01-14T01:01:01-06:00 Ububox /USR/SBIN/CRON[4733]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)
2008-01-14T01:02:01-06:00 Ububox /USR/SBIN/CRON[4744]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)
2008-01-14T01:03:01-06:00 Ububox /USR/SBIN/CRON[4755]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)
2008-01-14T01:04:01-06:00 Ububox /USR/SBIN/CRON[4766]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)
2008-01-14T01:05:01-06:00 Ububox /USR/SBIN/CRON[4777]: (root) CMD (/usr/local/sbin/phsal/crnsc.sh)
```
I see .../tnlwatch/crntlnl.sh being run at 00:30:01 (half past midnight), then I see .../phsal/crnsc.sh being run at 01:01:01, 01:02:01, 01:03:01, and so on.

Keep in mind that I am not an expert, so I could be wrong.
If you wanted to run crnsc.sh at 4 minuts past the hour, on the odd hours, I think you want this:
```
# m h dom mon dow command
<snip>
4 1,3,5,7,9,11,13,15,17,19,21,23 * * * /usr/local/sbin/phsal/crnsc.sh
```

That comment line at the top is a clue - the first column is the minute, the next the hour, and the last three are day of month, month, and day of week respectively.

You can learn more about this by typing this at a shell prompt:
```
man 5 crontab
```
Which leads to this line:
```
4 1-23/2 * * * /usr/local/sbin/phsal/crnsc.sh
```
which should run your command at 4 minutes after the hour, every odd hour.
However, looking around the web, using the earlier example, with 
all the odd hours listed, seems to be a more common practice.

-Ben

---

