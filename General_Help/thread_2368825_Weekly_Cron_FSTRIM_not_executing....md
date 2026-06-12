---
title: "Weekly Cron FSTRIM not executing..."
date: 2017-08-15
forum: General Help
---

### Post by badtlc on 2017-08-15
When I run FSTRIM manually it runs fine and has no issues.  The problem is I shouldn't be having to run this manually.   The weekly CRON job exists but it is not executing automatically.  How do I fix this?

SSD in question is an ADATA 250GB and 16.04.

Thanks.

---

### Post by QIII on 2017-08-15
Hello!

Is the job set up to create verbose log entries?  Are there no logs?

---

### Post by efflandt on 2017-08-15
Does fstrim normally provide any output. I actually moved the fstrim script to /etc/cron.daily, and when I run **sudo fstrim -a** there is no output. So maybe that means that my daily cron script is working.  If you do see output when you run fstrim manually, it could be that in a week there may be things like deleted files or rotated or compressed logs that left something for fstrim to do and report when run manually.```
~$ sudo hdparm -I /dev/sdb | grep TRIM
       *    Data Set Management TRIM supported (limit 8 blocks)
       *    Deterministic read ZEROs after TRIM
```

---

### Post by mc4man on 2017-08-16
By default fstrim doesn't log, (can be set up to), though you may see mention of cron.weekly running in one of your sys logs (on whatever day equates a week for you.

You could ck. cron.weekly as such - 
```
sudo run-parts /etc/cron.weekly -v
```

edit: to set up logging replace current fstrim in /etc/cron.weekly with 

```
#!/bin/sh
LOG=/var/log/trim.log
echo "*** $(date -R) ***" >> $LOG
fstrim -v / >> $LOG
```

---

### Post by badtlc on 2017-08-18
> **QIII said:**
> Hello!

Is the job set up to create verbose log entries?  Are there no logs?

I don't know that enabling logs will help as the job isn't executing so no log will be created.

Is there something that triggers cron that could be disabled?  I think the culprit might lie here as my system doesn't seem to auto-update weekly either.

---

