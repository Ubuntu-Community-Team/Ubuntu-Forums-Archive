---
title: "[Ubuntu 14.04 LTS] apparmor=&quot;DENIED&quot; for freshclam (CLAMAV)"
date: 2014-04-24
forum: General Help
---

### Post by matthys on 2014-04-24
Hello everyone,

I recently upgraded my Ubuntu server and notice some error messages regarding Apparmor and Freshclam.
So far I know I didn't had these error message with the previous version.

Syslog reports:
kernel: [  113.304926] type=1400 audit(1398085083.946:37): apparmor="DENIED"  operation="connect" profile="/usr/bin/freshclam" name="/run/clamav/clamd.ctl"  pid=2372 comm="freshclam" requested_mask="r" denied_mask="r" fsuid=110 ouid=110

Freshclam log reports:
WARNING: Clamd was NOT notified: Can't connect to clamd through /var/run/clamav/clamd.ctl

Any reason why freshclam may not read the clamd.ctl?

---

### Post by matthys on 2014-04-29
I also reported a bug-report for this as well, and has already been fixed: [https://bugs.launchpad.net/bugs/1313282](https://bugs.launchpad.net/bugs/1313282)

---

