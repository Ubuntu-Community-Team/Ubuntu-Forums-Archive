---
title: "cron bluez"
date: 2006-10-31
forum: General Help
---

### Post by SKF on 2006-10-31
Goodday,

i am having abit of cron issues

I have:

```
root in /etc/cron.allow
```

then i have:

```
35 20 1-5 * * /usr/sbin/backupDaily
30 1 * * Sunday /usr/sbin/backupSundayroot@
```

and the scripts don't have .sh extention

the scripts are all writeable.

this approce did not work

the other aprouce of adding script to 

```
/etc/crontab
``` now that does also not work !

any help please.

Thank you

---

