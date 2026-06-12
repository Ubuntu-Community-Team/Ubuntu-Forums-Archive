---
title: "Ubuntu 15.10 apparmor /run/ntpd.pid denied_mask=&quot;r&quot;"
date: 2016-06-29
forum: General Help
---

### Post by lance bermudez on 2016-06-29
When I login to my Ubuntu pc I get apparmor error denied r message
/var/log$ tail kern.log | grep denied
Jun 29 06:44:16 Tardis kernel: [  196.762638] audit: type=1400 audit(1467204256.961:29): apparmor="DENIED" operation="open" profile="/usr/sbin/ntpd" name="/run/ntpd.pid" pid=4559 comm="ntpd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Jun 29 06:44:16 Tardis kernel: [  196.762669] audit: type=1400 audit(1467204256.961:30): apparmor="DENIED" operation="open" profile="/usr/sbin/ntpd" name="/run/ntpd.pid" pid=4559 comm="ntpd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Jun 29 06:44:47 Tardis kernel: [  227.034701] audit: type=1400 audit(1467204287.229:31): apparmor="DENIED" operation="open" profile="/usr/sbin/ntpd" name="/run/ntpd.pid" pid=5221 comm="ntpd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Jun 29 06:44:47 Tardis kernel: [  227.034725] audit: type=1400 audit(1467204287.229:32): apparmor="DENIED" operation="open" profile="/usr/sbin/ntpd" name="/run/ntpd.pid" pid=5221 comm="ntpd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0

Why am I getting them now and how do I fix?

---

