---
title: "Getting an email from every job"
date: 2013-07-03
forum: General Help
---

### Post by Doles284 on 2013-07-03
On my home server running 12.10, I have a few things I want to set up email notifications for, mainly backups.

However, when I set up an smtp server, xmail or ssmtp, etc, I get an email for every job that the server does!

In crontab, I even suffix the jobs with ```
>> /dev/null
``` to push output to /dev/null, to no avail

I still get the full description of the job with >> /dev/null at the end :p

Is there some other notification system I could use? Or can I tell ssmtp to only be used by certain programs? I only want to know if a backup from backintime fails, that is all

Thanks all

---

### Post by DJ_Max on 2013-07-04
It should be

```
&> /dev/null
```

If you still get emails than it isn't cron sending you emails.

---

### Post by SeijiSensei on 2013-07-04
You can alternatively turn off emails globally in crontab, then use

```

1 2 3 4 * some_command 2>&1 | mail -s 'Running Backup' you@example.com

```

The "2>&1" ensures that any messages sent to syserr also get mailed to you.

---

