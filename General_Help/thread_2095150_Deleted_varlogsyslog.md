---
title: "Deleted /var/log/syslog"
date: 2012-12-16
forum: General Help
---

### Post by Hungry Man on 2012-12-16
So I was getting apparmor errors related to syslog so I rm'd it. Now I'm not getting any apparmor info from aa-logprof.

How do I fix that?

update: I figured it out:

service rsyslog restart
shutdown -r now

---

### Post by chadk5utc on 2012-12-16
Haha posted as I noticed it was solved

---

### Post by Hungry Man on 2012-12-16
The syslog. As in /var/log/syslog . But it's been solved.

---

