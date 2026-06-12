---
title: "broken /var/log/messages syslogd service"
date: 2008-01-07
forum: General Help
---

### Post by pirlouwi on 2008-01-07
While testing my Ubuntu Feisty, I broke my syslogd.
I cleaned manually /var/log/messages, and touch'ed the file.
Now it is no longer logging messages inside it.

I found in a RedHat forum that it could be the cause of SELinux, because the new /var/log/messages file I created has not the required security context.

:confused:
Is it true in my case?
If true, what is the command I should use to reconfigure /var/log/messages as it has to be?

Thx for support.
***.Pirlouwi.***

---

### Post by dcstar on 2008-01-08
> **pirlouwi said:**
> While testing my Ubuntu Feisty, I broke my syslogd.
I cleaned manually /var/log/messages, and touch'ed the file.
Now it is no longer logging messages inside it.

I found in a RedHat forum that it could be the cause of SELinux, because the new /var/log/messages file I created has not the required security context.

:confused:
Is it true in my case?
If true, what is the command I should use to reconfigure /var/log/messages as it has to be?

Thx for support.
***.Pirlouwi.***
Here is mine:
```
root@dc-desktop:/var/log# ls -al messages
-rw-r----- 1 syslog adm 361709 2008-01-09 10:36 messages
```
To fix:
```

cd /var/log
sudo chown syslog messages
sudo chgrp adm messages
sudo chmod 640 messages
```

---

