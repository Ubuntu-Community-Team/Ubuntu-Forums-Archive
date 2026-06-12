---
title: "Restarting of rsyslog"
date: 2015-07-16
forum: General Help
---

### Post by Sympatiko on 2015-07-16
Hi,

I have a zimbra cluster and I want to forward the zimbra logs to my log collector. Do you think its ok to restart the rsyslog? Is there any effect on the zimbra process?


Thanks,

---

### Post by Habitual on 2015-07-16
I wouldn't hesitate restarting syslog.
Zimbra is pretty smart and well written. It behaves rather well.

I'm interested in your .conf for the zimbra.log (or other in /opt/zimbra/log perhaps?)

Subscribed with interest.
Good Luck.

---

### Post by Sympatiko on 2015-07-18
Hi,

Actually the logs that I want to forward is /var/log/mail.log and /var/log/zimbra.log. Thanks for your tips.

---

### Post by Habitual on 2015-07-18
This is what I 'see' on those Zimbra files on my mail server:
```
-rw-r----- 1 syslog adm 26866629 Jul 18 12:28 /var/log/mail.log
-rw-r--r-- 1 syslog adm  1068812 Jul 18 12:29 /var/log/zimbra.log
```

so, the syslog facility 'owns' those 2 files and has read-write, so it is do-able.
Since zimbra has its own logging facility, it is not clear to me which if I should
write a new .conf in /etc/rsyslog.d/ or modify /etc/rsyslog.conf in some way.

On my mail host, zimbra user is a member of the adm group.
```
groups zimbra
zimbra : zimbra adm tty postfix

```

but I am in the same boat. I'd like to log those same files.
It hasn't become an issue, since we generally don't monitor our mail server logs by forwarding to another host,
in our case, Kibana, for analysis.

Don't be discouraged and sorry I didn't have a solution for you quickly.
Remember, it is do-able.

---

### Post by Sympatiko on 2015-07-21
No worries. Anything you said is appreciated. In my case I used splunk

---

