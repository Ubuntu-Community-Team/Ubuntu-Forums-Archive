---
title: "Spontaneous reboot?"
date: 2006-11-21
forum: General Help
---

### Post by paul cooke on 2006-11-21
About half an hour ago I came home from work and found myself logged out. On logging in, I discovered that uptime (shown on GKrellm) was only 1 hour. The power hasn't been interrupted (as the box would not have powered back up. The computer BIOS is set to stay off if that happens) and no one had been in the house.

Where can I look to see what could have caused the reboot?

---

### Post by Ramses de Norre on 2006-11-21
Look in /var/log/syslog or /var/log/messages.

But a kernel panic or something like that shouldn't cause a reboot.. Maybe overheating?

---

### Post by paul cooke on 2006-11-21
> **Ramses de Norre said:**
> Look in /var/log/syslog or /var/log/messages.

But a kernel panic or something like that shouldn't cause a reboot.. Maybe overheating?

messages:

Nov 21 06:41:17 localhost -- MARK --
Nov 21 07:01:17 localhost -- MARK --
Nov 21 07:21:18 localhost -- MARK --
Nov 21 07:39:14 localhost exiting on signal 15
Nov 21 07:39:15 localhost syslogd 1.4.1#17ubuntu7: restart.
Nov 21 07:59:15 localhost -- MARK --
Nov 21 08:19:15 localhost -- MARK --
Nov 21 08:39:15 localhost -- MARK --
Nov 21 08:59:16 localhost -- MARK --
Nov 21 09:19:16 localhost -- MARK --
Nov 21 09:39:16 localhost -- MARK --
Nov 21 09:59:16 localhost -- MARK --
Nov 21 10:19:17 localhost -- MARK --
Nov 21 10:39:17 localhost -- MARK --
Nov 21 10:59:17 localhost -- MARK --
Nov 21 11:19:18 localhost -- MARK --
Nov 21 11:39:18 localhost -- MARK --
Nov 21 11:59:18 localhost -- MARK --
Nov 21 12:19:18 localhost -- MARK --
Nov 21 12:39:19 localhost -- MARK --
Nov 21 12:59:19 localhost -- MARK --
Nov 21 13:19:19 localhost -- MARK --
Nov 21 13:39:19 localhost -- MARK --
Nov 21 13:59:20 localhost -- MARK --
Nov 21 14:19:20 localhost -- MARK --
Nov 21 14:39:20 localhost -- MARK --
Nov 21 14:59:20 localhost -- MARK --
Nov 21 15:18:01 localhost syslogd 1.4.1#17ubuntu7: restart.
Nov 21 15:18:01 localhost kernel: Inspecting /boot/System.map-2.6.15-25-686 

(I've not bothered with anything after that as that's the reboot time:

syslog gives no clues either...

Nov 21 07:39:15 localhost syslogd 1.4.1#17ubuntu7: restart.
Nov 21 07:39:18 localhost anacron[17140]: Job `cron.daily' terminated
Nov 21 07:39:18 localhost anacron[17140]: Normal exit (1 job run)
Nov 21 07:59:15 localhost -- MARK --
Nov 21 08:17:01 localhost /USR/SBIN/CRON[18577]: (root) CMD (   run-parts --report /etc/cron.hourly)
Nov 21 08:26:26 localhost postfix/smtp[18806]: D05D913E55C: to=<popcon@ubuntu.com>, relay=fiordland.ubuntu.com[82.211.81.145], delay=89140, status=deferred (host fiordland.ubuntu.com[82.211.81.145] said: 450 <root@localhost.localdomain>: Sender address rejected: Domain not found (in reply to RCPT TO command))
Nov 21 08:39:15 localhost -- MARK --
Nov 21 08:59:16 localhost -- MARK --
Nov 21 09:17:01 localhost /USR/SBIN/CRON[20027]: (root) CMD (   run-parts --report /etc/cron.hourly)
Nov 21 09:33:06 localhost postfix/smtp[20416]: D05D913E55C: to=<popcon@ubuntu.com>, relay=fiordland.ubuntu.com[82.211.81.145], delay=93140, status=deferred (host fiordland.ubuntu.com[82.211.81.145] said: 450 <root@localhost.localdomain>: Sender address rejected: Domain not found (in reply to RCPT TO command))
Nov 21 09:59:16 localhost -- MARK --
Nov 21 10:17:01 localhost /USR/SBIN/CRON[21478]: (root) CMD (   run-parts --report /etc/cron.hourly)
Nov 21 10:39:17 localhost -- MARK --
Nov 21 10:39:46 localhost postfix/smtp[22027]: D05D913E55C: to=<popcon@ubuntu.com>, relay=fiordland.ubuntu.com[82.211.81.145], delay=97140, status=deferred (host fiordland.ubuntu.com[82.211.81.145] said: 450 <root@localhost.localdomain>: Sender address rejected: Domain not found (in reply to RCPT TO command))
Nov 21 10:59:17 localhost -- MARK --
Nov 21 11:17:02 localhost /USR/SBIN/CRON[22928]: (root) CMD (   run-parts --report /etc/cron.hourly)
Nov 21 11:39:18 localhost -- MARK --
Nov 21 11:46:26 localhost postfix/smtp[23640]: D05D913E55C: to=<popcon@ubuntu.com>, relay=fiordland.ubuntu.com[82.211.81.145], delay=101140, status=deferred (host fiordland.ubuntu.com[82.211.81.145] said: 450 <root@localhost.localdomain>: Sender address rejected: Domain not found (in reply to RCPT TO command))
Nov 21 11:59:18 localhost -- MARK --
Nov 21 12:17:01 localhost /USR/SBIN/CRON[24379]: (root) CMD (   run-parts --report /etc/cron.hourly)
Nov 21 12:39:19 localhost -- MARK --
Nov 21 12:53:06 localhost postfix/smtp[25250]: D05D913E55C: to=<popcon@ubuntu.com>, relay=fiordland.ubuntu.com[82.211.81.145], delay=105140, status=deferred (host fiordland.ubuntu.com[82.211.81.145] said: 450 <root@localhost.localdomain>: Sender address rejected: Domain not found (in reply to RCPT TO command))
Nov 21 13:17:02 localhost /USR/SBIN/CRON[25831]: (root) CMD (   run-parts --report /etc/cron.hourly)
Nov 21 13:39:19 localhost -- MARK --
Nov 21 13:59:20 localhost -- MARK --
Nov 21 13:59:46 localhost postfix/smtp[26863]: D05D913E55C: to=<popcon@ubuntu.com>, relay=fiordland.ubuntu.com[82.211.81.145], delay=109140, status=deferred (host fiordland.ubuntu.com[82.211.81.145] said: 450 <root@localhost.localdomain>: Sender address rejected: Domain not found (in reply to RCPT TO command))
Nov 21 14:17:01 localhost /USR/SBIN/CRON[27282]: (root) CMD (   run-parts --report /etc/cron.hourly)
Nov 21 14:39:20 localhost -- MARK --
Nov 21 14:59:20 localhost -- MARK --
Nov 21 15:06:27 localhost postfix/smtp[28481]: D05D913E55C: to=<popcon@ubuntu.com>, relay=fiordland.ubuntu.com[82.211.81.145], delay=113141, status=deferred (host fiordland.ubuntu.com[82.211.81.145] said: 450 <root@localhost.localdomain>: Sender address rejected: Domain not found (in reply to RCPT TO command))
Nov 21 15:17:02 localhost /USR/SBIN/CRON[28738]: (root) CMD (   run-parts --report /etc/cron.hourly)
Nov 21 15:18:01 localhost syslogd 1.4.1#17ubuntu7: restart.
Nov 21 15:18:01 localhost kernel: Inspecting /boot/System.map-2.6.15-25-686

deity knows what all that rejected mail is for... I've never known popcon to work properly.

---

### Post by Nevell on 2008-05-19
Anybody fix this trouble?

---

