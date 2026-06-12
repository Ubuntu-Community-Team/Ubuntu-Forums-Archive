---
title: "running cron job"
date: 2014-09-11
forum: General Help
---

### Post by sniper8752 on 2014-09-11
I am trying to run motion as a cron task.  I was not able to get it to work, so I modified it to this instead of a particular time:
```
* * * * * /etc/initd./motion start
```
I modified it by typing in sudo crontab -e.  In the syslog, all I get is this:
```
(root) CMD (/etc/init.d/motion start
```
Over and over again.  Yet, motion does not start.  Any ideas on how I can get this to run?

---

### Post by ian-weisser on 2014-09-11
Is 'motion' an application or a service or a daemon?

Have you checked ps to ensure it's not running? The syslog entry you posted seems to imply that it started, as you told it to.

Does it really have an /etc/init.d entry? That would imply it's a service or a daemon, and perhaps inappropriate to start from cron.

Does 'motion' require any particular dependencies to be running before start? Any environment variables?

---

