---
title: "Crontab"
date: 2008-04-25
forum: General Help
---

### Post by Maky001 on 2008-04-25
I need to execute script every 5 minutes so think that cron will do the job.
But not yet working with him so please help.
Would this be ok
*/5 * * * * /var/bin/status.sh >>/var/tmp/status.log 2>&1

so every 5 minutes it execute script status.sh from var/bin and make log in var/tmp status.log.

Please correct me if i am wrong.

THX!!!!

---

### Post by StevenHarper on 2008-04-25
Here is my Crontab entry that runs every 5 mins

```
0,5,10,15,20,25,30,35,40,45,50,55 * * * *  /usr/local/scripts/ascript.sh > /tmp/alog.out
```

Steve

---

### Post by kpkeerthi on 2008-04-25
> **Maky001 said:**
> I need to execute script every 5 minutes so think that cron will do the job.
But not yet working with him so please help.
Would this be ok
*/5 * * * * /var/bin/status.sh >>/var/tmp/status.log 2>&1

so every 5 minutes it execute script status.sh from var/bin and make log in var/tmp status.log.

Please correct me if i am wrong.

THX!!!!

Perfect. Although I would put a [space] after >> for better readability.

---

