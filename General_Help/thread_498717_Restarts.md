---
title: "Restarts"
date: 2007-07-11
forum: General Help
---

### Post by theQmaster on 2007-07-11
Hello,

Since I've upgraded from 5.04->5.10->6.06 I noticed that my logcheck send me some emails about restarts.
Anyone knows if there is a bug in the current release. Usually happens at night or early morning.

This is the message I get
server syslogd 1.4.1#18ubuntu6: restart.

I have to look the logs up to extract the logs prior to the restart message and then paste them here before doing that anyone know of any issues in the current 6.06 ? Some people were talking about some bugs in the core.

[https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/81713](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/81713)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/68338](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/68338)

Thanks
Q

Ps.
Is there an official site were we can see the bugs reported on 6.06 or later versions ?
:confused:

---

### Post by theQmaster on 2007-07-11
**It looks like it's an anacron problem ! Every time when server restarts it's due to signal15 while running cron.daily**


Jul  9 07:30:01 server /USR/SBIN/CRON[17007]: (root) CMD (test -x /etc/init.d/anacron && /usr/sbin/invoke-rc.d anacron start >/dev/null)
Jul  9 07:30:01 server anacron[17032]: Anacron 2.3 started on 2007-07-09
Jul  9 07:30:01 server anacron[17032]: Will run job `cron.daily' in 5 min.
Jul  9 07:30:01 server anacron[17032]: Jobs will be executed sequentially
Jul  9 07:35:01 server anacron[17032]: Job `cron.daily' started
Jul  9 07:35:01 server anacron[17044]: Updated timestamp for job `cron.daily' to 2007-07-09
Jul  9 07:35:02 server exiting on signal 15

**The log after restarts looks like this**

Jul  9 07:35:03 goodstockimages syslogd 1.4.1#18ubuntu6: restart.
Jul  9 07:35:03 goodstockimages anacron[17032]: Job `cron.daily' terminated
Jul  9 07:35:03 goodstockimages anacron[17032]: Normal exit (1 job run)
Jul  9 07:45:01 goodstockimages /USR/SBIN/CRON[17163]: (root) CMD (/usr/local/awstats/tools/awstats_updateall.pl now >> /var/log/awstats.log)
Jul  9 07:55:03 goodstockimages -- MARK --

---

### Post by theQmaster on 2007-07-16
so... is this a restart of not ? It happens eveery day at 7:35:02 and if I look thru the logs it may not be a restart ? the message is very misleading.

---

### Post by Sporkman on 2007-11-12
> **theQmaster said:**
> so... is this a restart of not ? It happens eveery day at 7:35:02 and if I look thru the logs it may not be a restart ? the message is very misleading.

I get the same thing, at 7:35 daily as well. It doesn't appear to be a full reboot, because syslog doesn't have the huge amount of messages you get when a reboot occurs, it appears to be apache restarting. What I do see is anacron starting right beforehand, however I don't have any actual cron jobs set for around that time...

---

