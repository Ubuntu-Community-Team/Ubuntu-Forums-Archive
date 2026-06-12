---
title: "Interesting cron behavior (Ubuntu Server 12.04.4)"
date: 2014-01-14
forum: General Help
---

### Post by DigiAngel on 2014-01-14
So I have a user cron that runs this:

* 3 * * 1-5 /opt/bin/wol

This should fire off at 03:00 once.  Instead, it fires off every minute as shown with my cron emails:
Jan 14 03:00:01 gateway CRON[2698]: (me) CMD (/opt/bin/wol)
Jan 14 03:01:01 gateway CRON[2941]: (me) CMD (/opt/bin/wol)
[redacted]
Jan 14 03:58:02 gateway CRON[7302]: (me) CMD (/opt/bin/wol)
Jan 14 03:59:01 gateway CRON[7329]: (me) CMD (/opt/bin/wol)

my actual /etc/crontab file:
# m h dom mon dow user  command
1 *     * * *   root    cd / && run-parts --report /etc/cron.hourly
1 0     * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
1 0     * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
1 0     1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
58 23     * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.reports )
0-59/5 * * * *  root    /usr/local/bro/bin/broctl cron

Anything I can do to troubleshoot this weird behavior?  Thank you.

---

### Post by ian-weisser on 2014-01-14
> **DigiAngel said:**
> 

* 3 * * 1-5 /opt/bin/wol

This should fire off at 03:00 once.

It should fire off each minute during the 3 hour, since the minute field is a '*'. 
From your description, that's what it's properly doing.

If you want it to fire off just once, specify a minute also:

0 3 * * 1-5 /opt/bin/wol

---

### Post by DigiAngel on 2014-01-14
Ah darn...nice catch thanks Ian.  This will most likely fix it right up :)  Thanks again.

---

