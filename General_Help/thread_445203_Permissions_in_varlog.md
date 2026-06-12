---
title: "Permissions in /var/log"
date: 2007-05-15
forum: General Help
---

### Post by artesvida on 2007-05-15
I'm using smsclient (or sms_client, if you prefer) and periodically the log file (/var/log/smsclient.log) is re-created with permissions 660.  I have a script that needs the permissions to be 666, so I chmod the log file and all is good until smsclient decides to re-create the log file and set the permissions back to 660.

How can I make this change stick?  I see that log files in /var/log have different ownerships and permissions -- how are the permissions in /var/log determined?  By the application that uses them?  If so, does that mean I need to wade through the smsclient source code?

---

### Post by kidders on 2007-05-17
Hi there,

There are various ways files in /var/log might be created. Before wandering around your smsclient configuration, take a look at logrotate's. What you need might be in there.

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

### Post by artesvida on 2007-05-17
THANK YOU!!!  It wasn't in /etc/logrotate.conf, nor was it in /etc/logrotate.d/, but this suggestion got me looking at cron jobs, and in cron.weekly there is an entry for smsclient that uses savelog to save the old log and create a new one.

---

### Post by kidders on 2007-05-17
Excellent. :-)

That's perfectly sensible, because not all applications will necessarily be smart enough to detect & exploit the presence of **logrotate** on a system.

Glad you found what you needed!

---

