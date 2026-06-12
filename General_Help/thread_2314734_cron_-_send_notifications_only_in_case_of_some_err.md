---
title: "cron - send notifications only in case of some error"
date: 2016-02-23
forum: General Help
---

### Post by marchello_lippi2 on 2016-02-23
Hi all, 

I got some crontab records and everything works fine. 
I installed mail server recently and all cron notifications started to come into my inbox. 
I'd like to receive only notifications about cron errors.  
I would rather not filter all notifications off.
Is it possible at all?
Thanks ahead. 

lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:        14.04
Codename:       trusty

---

### Post by TheFu on 2016-02-23
Yes, you can make the cron-jobs send an email with the error, but it isn't just built-into cron. At least I don't think it is. 
Most places redirect cron-job standard output to /dev/null and let stderr go the normal way.  Or you could handle INFO/WARNING/ERROR messages inside the script that is run from the crontab and only email something (forgetting anything about cron for the email).

[https://serverfault.com/questions/226074/cron-only-get-errors-in-emails](https://serverfault.com/questions/226074/cron-only-get-errors-in-emails) has an example that redirects stdout, but not stderr.
```
MAILTO=email@example.com
0 */2 * * * /bin/backup.sh > /dev/null
``` Of course, any scripts would need to send errors to stderr and info to stdout. That's normal practice for Unix systems.

According to the cron manpage, there is a way to control the logging level, but this is about what is written to syslog, not what gets emailed.  Wouldn't hurt to review it.

Google found this: [http://habilis.net/cronic/](http://habilis.net/cronic/) - I've never used it and the examples do not follow "best practices" for scripting.  Shush and cronwrap seem to be other options. Never used any of those.

Sorry I'm not any real help.

---

### Post by marchello_lippi2 on 2016-02-23
Thanks [[COLOR=#000000]TheFu[/COLOR]]("http://ubuntuforums.org/member.php?u=1037685")[COLOR=#000000] [/COLOR]

---

