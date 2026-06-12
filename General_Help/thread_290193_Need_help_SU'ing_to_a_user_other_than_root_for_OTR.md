---
title: "Need help SU'ing to a user other than root for OTRS install"
date: 2006-10-31
forum: General Help
---

### Post by txgeek on 2006-10-31
Part of the OTRS install requires that you run a script as the OTRS user.  To do this you are supposed to login as root, then 'su otrs'.  After which you should be able to run a script that adds some cron jobs to the crontab for the user OTRS.

Whenever I issue the command 'su otrs' it executes without any errors.  But if I issue the command whoami it still tells me I am root, and I am unable to run the script that adds the cron jobs as it detects I am not the OTRS user.

Is there some special configuration change I need to make before I can SU to a user other than root?

---

### Post by jpkotta on 2006-10-31
Try ```
su - otrs
```

or using sudo,
```
sudo -i -u otrs
```

For reference:
```
man su
man sudo
```

---

