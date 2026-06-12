---
title: "Weird Crontab Problem"
date: 2005-09-30
forum: General Help
---

### Post by AJStiles on 2005-09-30
I'm having strange problems with a user's crontab.
Using crontab -e when running as the user, I create this entry:
```

* * * * * echo "Hello world"

```
or 
```

* * * * * /path/to/script

```
Gives me this error in syslog:
```

Sep 30 10:15:01 localhost /USR/SBIN/CRON[7472]: (CRON) error (do_command:setuid(1000) failed: Resource temporarily unavailable)

```
I've tried lots of things, but crontab doesn't seem to want to run. Any ideas?
AJS

---

