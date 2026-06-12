---
title: "Is this bad???"
date: 2008-07-07
forum: General Help
---

### Post by DaleHUtch on 2008-07-07
I have this line appearing in my syslogs. Is it bad or normal operations?

Jul  7 11:09:01 WormHole6 /USR/SBIN/CRON[14794]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)



Thanks!

DH

---

### Post by HalPomeranz on 2008-07-07
What the command is doing is deleting files under /var/lib/php5 that are older than the number of minutes configured in /usr/lib/php5/maxlifetime.  Seems like a normal operational job to me.

What are the contents of /var/lib/php5 on your machine?

---

### Post by DaleHUtch on 2008-07-07
Thanks for the help!

Linux is new to me and I love it!

---

