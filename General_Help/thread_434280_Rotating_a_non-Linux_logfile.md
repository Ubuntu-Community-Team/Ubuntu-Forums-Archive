---
title: "Rotating a non-Linux logfile?"
date: 2007-05-05
forum: General Help
---

### Post by william_hunter on 2007-05-05
OK, I suppose I should explain that..

The game server I run uses a wrapper program that generates a logfile named nwnx_chat. I would like to rotate this logfile with a time/datestamp every night at approximately the same time. Can this be done?

---

### Post by yabbadabbadont on 2007-05-05
You could probably configure logrotate to do it.  If not, a simple shell script and a crontab entry would handle it.

---

### Post by william_hunter on 2007-05-06
logrotate is a program already on the machine, I take it? I run Ubuntu Edgy, FYI.

---

### Post by yabbadabbadont on 2007-05-06
It should be.  It is configured through /etc/logrotate.conf and files in /etc/logrotate.d/  You'll need to read the logrotate manpage for details.

---

### Post by william_hunter on 2007-05-09
Thanks

---

