---
title: "wtmp log file erased"
date: 2007-09-04
forum: General Help
---

### Post by smmathew on 2007-09-04
I recently used the last command to find out who had been logged in lately and it only shows me logged in currently. Up until now I have been able to use last and get a long list of logins.... What happened?

---

### Post by grandsatrap on 2008-01-12
This is happening to me too.  
Every few weeks wtmp gets cleared. There is a file  /var/log/wtmp.1  but it only goes back for 1 month. Some default setting in ubuntu must be doing this. What a dumb idea. I think it is important to have a record of who has logged onto your system.

I'd love to find out how to fix it.  My guess is something in logrotate.

---

### Post by andrew.46 on 2008-01-29
Hi,

 Saw your message about logrotate:

> **grandsatrap said:**
> This is happening to me too.  
Every few weeks wtmp gets cleared. There is a file  /var/log/wtmp.1  but it only goes back for 1 month. Some default setting in ubuntu must be doing this. What a dumb idea. I think it is important to have a record of who has logged onto your system.

I'd love to find out how to fix it.  My guess is something in logrotate.

Well, it is quite easy to alter these settings. Open logrotate.conf:

```
$ gksudo gedit /etc/logrotate.conf
```

The settings for wtmp in Feisty are these:

```
/var/log/wtmp {
    missingok
    monthly
    create 0664 root utmp
    rotate 1
}
```

So the wtmp log is backed up every month, a new copy is created and the backup copy is kept for 1 month and then deleted. If you wanted to keep longer records you could keep backups for 6 months by asking for:

```
rotate 6
```

Is this what you were after?

             Andrew

---

