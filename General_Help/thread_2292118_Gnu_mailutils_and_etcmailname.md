---
title: "Gnu mailutils and /etc/mailname"
date: 2015-08-25
forum: General Help
---

### Post by Kjeld Flarup on 2015-08-25
Hi

With Ubuntu 10.04 and 12.04 I used to write viptel.dk in /etc/mailname to make mail utils use @viptel.dk
But with 14.04.3 this is ignored. Instead the hostname is used, but I do not want to call all my servers viptel.dk

I have not been able to search out how to do it now, all recipies says to use /etc/mailname

Anyone know what has changed, and what to do now.

---

### Post by Kjeld Flarup on 2015-08-26
This did the trick as it throws the local away from local.viptel.dk
masquerade_domains = viptel.dk

Or more generic since $myorigin is by default read from /etc/mailname
masquerade_domains = viptel.dk

---

