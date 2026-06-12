---
title: "apparmor stops clamav-daemon service from starting"
date: 2021-09-09
forum: General Help
---

### Post by pcla56 on 2021-09-09
I am running 20.04 and in the past few days the service won't start.

In syslog I can see:

Sep  9 15:07:45 ikserver2 kernel: [  930.739353] audit: type=1400  audit(1631196465.535:17): apparmor="DENIED" operation="capable"  profile="/usr/sbin/clamd" pid=1334 comm="clamd" capability=0   capname="chown"

This seems to be stopping a lchown to clamav on the log file /var/log/clamav/clamav.log which then causes the service to fail.

How can I fix this please?

Thx Paul

---

### Post by &amp;KyT$0P# on 2021-09-09
Check the output of
```
ls -la /var/lib/clamav
```
The owner/group for that folder should be [FONT=Courier New]clamav:clamav[/FONT] and the log files inside that folder should be owner/group [FONT=Courier New]clamav:adm[/FONT] .  If it's not this way for you, does it fix the problem if you manually chown to match that?

---

