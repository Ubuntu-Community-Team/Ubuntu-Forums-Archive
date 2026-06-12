---
title: "Cron, Anacron, and Flexbackup - Why don't my jobs run?"
date: 2008-04-26
forum: General Help
---

### Post by coolaj86 on 2008-04-26
Given: Ubuntu 8.04 is currently installed

Given: This was my process a few months ago.
```
apt-get install flexbackup

cat - > /etc/cron.monthly/flexbackup.full
#!/bin/bash
/usr/bin/flexbackup -set all -full
EOF

chown root:root /etc/cron.monthly/flexbackup.full
chmod a+rx /etc/cron.monthly/flexbackup.full

cat - > /etc/cron.weekly/flexbackup.diff
#!/bin/bash
/usr/bin/flexbackup -set all -differential
EOF

chown root:root /etc/cron.weekly/flexbackup.diff
chmod a+rx /etc/cron.weekly/flexbackup.diff

cat - > /etc/cron.daily/flexbackup.incr 
#!/bin/bash
/usr/bin/flexbackup -set all -incremental
EOF

chown root:root /etc/cron.daily/flexbackup.incr 
chmod a+rx /etc/cron.daily/flexbackup.incr 

vim /etc/flexbackup.conf #Edited to taste
```

Desired result:
backups should occur every day, week, month as incremental, differential, full respectively

Actual result:
it has never worked once
no backups are performed

Troubleshooting:
```
grep -iR 'flexbackup' /var/log
```
Returns only info about the initial installation procedure
In fact there doesn't seem to be any log showing any of cron's or anacron's success or failures.

Running this command by hand works perfectly
```
/etc/cron.monthly/flexbackup.full
```
the logrotate script in /etc/cron.daily works perfectly

Question:
How can I make cron / anacron perform the jobs I set up as root?

---

### Post by Tm Tecnos on 2010-01-15
Hello coolaj86
dunno if this can help, probably you solved already.

Anyway I thought to post here my experience, maybe it will be useful for someone.

I had the same problem and I found that, probably after an update of Ubuntu, there was a difference between the PATH= line in crontab and the PATH of the root user for an interactive login, this was what made my flexbackup script working perfectly in interactive mode but not when launched by crontab.

I checked the PATH of the interactive root shell this way:
sudo bash
echo $PATH

Then I updated the PATH= line at the beginning of the /etc/crontab file with the same settings as before and everything started working again.

Happy Ubuntu!
Tom

---

