---
title: "mail and cron"
date: 2007-01-16
forum: General Help
---

### Post by capnqwest on 2007-01-16
Do I need to setup a whole mail server just to have crond e-mail me the output of a cron?

my rsync cron script calls for a mail -s but when the cron runs, I get tons of errors that basically say invalid hostname (my hostname is mint.fluxcapacitor.org).

I'm running a default install of edgy and haven't installed any mail packages.

Here is my crontab entry:
```
59 24 * * * michael /home/michael/amy_rsync.sh 2>&1 | mail -s "Amy's rsync script" michael@localhost
```

Oddly though, I cannot call mail from the cli.  I'm an Ubuntu newbie but not a Linux newbie.  TIA.

---

