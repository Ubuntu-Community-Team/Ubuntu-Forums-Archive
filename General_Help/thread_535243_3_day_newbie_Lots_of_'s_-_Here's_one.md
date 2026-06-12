---
title: "3 day newbie Lots of ?'s - Here's one"
date: 2007-08-26
forum: General Help
---

### Post by posterboy on 2007-08-26
It appears (to me) that /var/log/mail.log and /var/log/mail.info are identical. Why are we logging twice?

---

### Post by quux on 2007-08-26
Have a look at "/etc/syslog.conf" - this is where the logging rules for syslog are defined. "mail.log" is the combination of "mail.err", "mail.warn" and "mail.info".

---

### Post by posterboy on 2007-08-26
AHHH, thank you, it's split up, in .info, all together in .log.

---

