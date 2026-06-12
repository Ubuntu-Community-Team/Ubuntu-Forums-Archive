---
title: "Logwatch not working after hostname change"
date: 2016-07-15
forum: General Help
---

### Post by SchnappiJedi on 2016-07-15
After changing the hostname by editing the following files:
/etc/hosts
/etc/hostname
/etc/postfix/main.cf

and restarting Logwatch is still sending emails to "root@**oldhost**.com" (as seen in /var/log/mail.log). 

/etc/logwatch/conf/logwatch.conf & /usr/share/logwatch/default.conf/logwatch.conf both list:
MailTo = root

Guess could change this but don't get why root isn't getting translated correctly. 

"echo "test message" | mailx -s 'test subject' [EMAIL="demo@demo.com"]demo@demo.com[/EMAIL]" works fine. Sends as [EMAIL="root@newhost.com"]root@newhost.com[/EMAIL].

---

### Post by Habitual on 2016-07-15
```
cat /etc/aliases
```
show anything unusual?

---

### Post by SchnappiJedi on 2016-07-15
> **Habitual said:**
> ```
cat /etc/aliases
```
show anything unusual?

No.

Furthermore replicated this on multiple machines.

---

### Post by SchnappiJedi on 2016-07-16
Editing /etc/mailname (should) resolve the issue.

When changing a hostname /etc/mailname should be changed as well.

---

