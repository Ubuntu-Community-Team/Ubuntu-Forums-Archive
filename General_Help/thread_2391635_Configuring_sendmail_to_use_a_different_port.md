---
title: "Configuring sendmail to use a different port"
date: 2018-05-11
forum: General Help
---

### Post by sniper8752 on 2018-05-11
I am trying to use port 587 with comcast to use sendmail to get mail out.  I've added these lines to my sendmail.mc file:
```
define(`SMART_HOST',`**smtp.comcast.net**`)dnldefine(`RELAY_MAILER',`esmtp')dnl define(`RELAY_MAILER_ARGS', `TCP $h 587')dnl
```
I ran:
```
m4 sendmail.mc > sendmail.cf
```
then restarted sendmail, and it still doesn't work.  Checking on the status of sendmail, I notice this:
```
May 11 12:52:51 hostname sm-mta[16834]: w4BIqpMa016834: w4BIqpMb016834: return to sender: Host unknown (Name server: y: host not found)May 11 12:52:51 hostname sm-mta[16834]: w4BIqpMb016834: to=postmaster, delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=30000, relay=y, dsn=5.1.2, stat=Host unknown (Name server: y: host not found)

```
Could this be the cause of the mail not being sent out successfully?

---

### Post by sniper8752 on 2018-05-11
It seems that the value, $h comes out to by "y".

---

