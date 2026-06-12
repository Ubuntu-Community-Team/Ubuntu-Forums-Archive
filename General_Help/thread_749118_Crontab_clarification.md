---
title: "Crontab clarification"
date: 2008-04-08
forum: General Help
---

### Post by loryguru on 2008-04-08
Dear All,
I'm new to linux and today I was looking into a crontab file in a server I "inherited" :)

I found this line:
00 */1 * * * root /root/scripts/scriptname

Could someone clarify the meaning of "*/1" syntax?
Thanks in advance.
Regards to all :)
Lorenzo M.

---

### Post by MrEgg on 2008-04-08
Hi,

I think it stands for every 1 hour, on the hour in this case.

Likewise, a crontab specifying */5 8-20 * * * would execute the command every 5 minutes, from 8am to 8pm.

Regards,
Egg

---

### Post by loryguru on 2008-04-08
Thanks a lot Egg.
Regards.
lory-the-guru

---

