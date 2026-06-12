---
title: "Domain of Sender does not exist"
date: 2007-01-15
forum: General Help
---

### Post by cssutto on 2007-01-15
I am having a problem with messages that are created by rkhunter and various other utilities that use cron to send messages to indicate their successes or failures.

syslog shows the "domain of sender xxxx " does not exist.

I have no problems with real email, sending or receiving, only with messages that are internal cron types.

What appears to be happening is that an extra domain name is appended to the correct address.

For instance if the real address is [email]xxxx@xxx.xxx[/email], the name rejected is shown as [email]xxxx@xxx.xxx.xxxx.xxx[/email]

If it helps, I use nullmailer and mutt for email.

Postfix instead of sendmail.

For some reason, I suspect postfix, but I have not been able to find the problem.

It is only a minor annoynace, but I would like to fix it because when the messages are refused, they go back to /var/spool/nullmailer/queue and nullmailer repeatedly tries to empty the queue, resulting in syslog getting filled up with repeat "domain of sender" messages.

How do I fix?

CSSJR

---

