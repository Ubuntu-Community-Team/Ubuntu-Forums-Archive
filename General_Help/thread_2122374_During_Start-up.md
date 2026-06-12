---
title: "During Start-up"
date: 2013-03-05
forum: General Help
---

### Post by johnryaniii on 2013-03-05
I notice during start up my ubuntu linux runs a program call "MTA."

Now my problem is locating this program MTA and removing it.

How do i find out where MTA is located and stop it from starting up during boot up.

Thanks.

---

### Post by lechien73 on 2013-03-05
Normally when Ubuntu refers to "MTA" on startup, it's the "Mail Transport Agent", which is likely sendmail or postfix.

Often some other application depends on the mail transport agent, so in that case you wouldn't really want to remove it. If it appears to be slowing down your startup, then that could be because it's having trouble resolving your host name. If that's the issue, then please post back and we'll help you to fix it.

---

