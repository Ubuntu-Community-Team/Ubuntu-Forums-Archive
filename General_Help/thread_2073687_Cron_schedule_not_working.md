---
title: "Cron schedule not working"
date: 2012-10-20
forum: General Help
---

### Post by Charlietje on 2012-10-20
Hi,

I have a cron task (backup script) that I want to execute every monday, except the first monday of the month.

this is the crontab snippit:


```

05 09 1-7  * mon root	/backup/backup_xcube -f
01 09 8-31 * mon root	/backup/backup_xcube -i

```


But the script backup_xcube -i get executed every day!
The backup_xcube -f did not execute yet.

Can someone help me explain why it gets executed?

I tried replacing "mon" by "1" but it also executed every day.

I restarted the crontab daemon, but still the same.
I'm running Ubuntu 12.04

Regards
Carl

---

### Post by papibe on 2012-10-20
Hi Charlietje.

Cron uses either the dom or dow to choose which day will execute the command. However when both are set (not *), you'll end up with an 'OR' rule.

In your case, 'backup_xcube -i' is executing from 8th to 31st, **and** all Mondays.

In order to accomplish what you want, I would recommend set cron to run every monday and then have a bash code like this:
```
01 09 * * mon  root  [ $(date +%e) -gt 7 ] && backup_xcube -i
```
I hope that points you in the right direction. Let us know how it goes.
Regards.

---

### Post by Charlietje on 2012-10-20
Papibe,


Your solution did point me to the right direction.


Thanks for that!

---

