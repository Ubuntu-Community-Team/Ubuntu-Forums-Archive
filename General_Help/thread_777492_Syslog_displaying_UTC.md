---
title: "Syslog displaying UTC"
date: 2008-05-01
forum: General Help
---

### Post by awacs on 2008-05-01
In a new installation of 7.10, the date displayed is correct:
Thu May  1 12:52:33 EDT 2008

But syslog (and the other logs) think in terms of UTC:
May  1 16:53:11 chocolate postfix/qmgr[5594]: AEFC26A41EB: removed

How do I fix this?

Thanks!

---

### Post by awacs on 2008-05-01
Never mind! I found it. It's in /etc/default/rcS.

---

