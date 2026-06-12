---
title: "sendmail - runq - not forcing mail"
date: 2008-02-13
forum: General Help
---

### Post by OnyxDragun on 2008-02-13
When using sendmail along with PHP mail enters the queue with no issue. But it takes forever for the queue to be processed (like 10minutes) and using runq or sendmail -q -v doesn't do anything.

mailq just shows the message waiting there. Eventually it gets processed.

/etc/mail/sendmail.conf

DAEMON_MODE="Daemon";

QUEUE_MODE="${DAEMON_MODE}";
QUEUE_INTERVAL="2m";
QUEUE_PARMS="";

MSP_MODE="Daemon";
MSP_INTERVAL="2m";
MSP_PARMS="";

Would be the basic stats I have for the config file. I've reloaded the /usr/sbin/sendmailconfig file to reload the config etc and I have also restared /etc/init.d/sendmail but still the mail gets queue.

When I try to force the queue I get this:
/etc/mail$ sudo sendmail -q -v

Running /var/spool/mqueue/m1DKaPxk013908 (sequence 1 of 1)
m1DKaPxk013908: locked

Other than going to another program for sending mail out via php... what am I forgetting to do for the queue to process properly at the set interval I want?

Thanks

---

