---
title: "dual syslog entries??"
date: 2008-03-27
forum: General Help
---

### Post by b4nsh33 on 2008-03-27
Hi to all, i  just installed a smtp filter using postfix/amavis/spamassassin, so far so good, i have activated a high loglevel in each one to do postprocessing reports and statistics, etc.
the "problem" that im facing is that syslog adds entries twice, one in /var/log/syslog and another in /var/log/mail.log, in the amavis and postfix forum everybody recomends faster disks, log to a dedicated syslog server, etc, beacuse hard disk i/o can be a serius problem for a high load email server, im afraid that adding two entries for each event will hurt overall performance of my filter.
is this normal and if so, why is this configured default?
how can i disable it?
i want all email (postfix, amavis, spamassassin) related events go just to /var/log/mail.log where it makes sense to go, not to /var/log/syslog where only system events should (allegedly) go, like in another distributions.
regards

---

### Post by dcstar on 2008-03-27
> **b4nsh33 said:**
> Hi to all, i  just installed a smtp filter using postfix/amavis/spamassassin, so far so good, i have activated a high loglevel in each one to do postprocessing reports and statistics, etc.
the "problem" that im facing is that syslog adds entries twice, one in /var/log/syslog and another in /var/log/mail.log, in the amavis and postfix forum everybody recomends faster disks, log to a dedicated syslog server, etc, beacuse hard disk i/o can be a serius problem for a high load email server, im afraid that adding two entries for each event will hurt overall performance of my filter.
is this normal and if so, why is this configured default?
how can i disable it?
i want all email (postfix, amavis, spamassassin) related events go just to /var/log/mail.log where it makes sense to go, not to /var/log/syslog where only system events should (allegedly) go, like in another distributions.
regards

```
man syslog.conf
```

---

### Post by b4nsh33 on 2008-03-28
ok, i know how to change it, but why is this default?
Waste a write disk operation, duplicate everything ?????
It's Not the best design, isnt it?
is there a package mantainer anywhere here?

---

