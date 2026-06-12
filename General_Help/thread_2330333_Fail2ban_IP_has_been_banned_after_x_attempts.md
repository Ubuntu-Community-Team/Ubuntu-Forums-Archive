---
title: "Fail2ban IP has been banned after x attempts"
date: 2016-07-10
forum: General Help
---

### Post by SchnappiJedi on 2016-07-10
Turned on email messages when an IP banned and got many emails saying things like this:

"The IP X.X.X.X has just been banned by Fail2ban after 1214 attempts against SSH."

Fail2ban maxretry was set to two, so why does the email say that IP are banned after more than two attempts?

---

### Post by Skaperen on 2016-07-10
1214 failures detected exceeds the limit of 2.  this does not mean it gets to report on every try like on try 3

---

### Post by mastablasta on 2016-07-11
> **SchnappiJedi said:**
> Turned on email messages when an IP banned and got many emails saying things like this:

"The IP X.X.X.X has just been banned by Fail2ban after 1214 attempts against SSH."

Fail2ban maxretry was set to two, so why does the email say that IP are banned after more than two attempts?


each service (SSH, apache, email...) has it's own setting. make sure they are set up well.

also make sure you are not unbanning them. the ban time should be long. at least a year.

---

### Post by Habitual on 2016-07-11
My first guess is that they (the IP) are being rapidly unbanned.
I need two outputs to help:
```
fail2ban-client get ssh maxretry
fail2ban-client get ssh bantime
```

---

### Post by SchnappiJedi on 2016-07-15
fail2ban-client get sshd maxretry
2

fail2ban-client get sshd bantime
2592000

The SSH jail is called "sshd" by default at least in 14 & 16 LTS, not "ssh."

---

### Post by SchnappiJedi on 2016-07-16
Editing /etc/mailname (should) resolve the issue.

When changing a hostname /etc/mailname should be changed as well.

**Disregard above. Should have been posted here: [https://ubuntuforums.org/showthread.php?t=2330830&p=13517782](https://ubuntuforums.org/showthread.php?t=2330830&p=13517782)**

---

### Post by Habitual on 2016-07-16
> **SchnappiJedi said:**
> Editing /etc/mailname (should) resolve the issue.

When changing a hostname /etc/mailname should be changed as well.
Your other thread perhaps, methinks.

Try bantime = 600
you know, the default. It works **out of the box?**

2592000 seconds?
Always start with defaults?

```
fail2ban-client set sshd bantime 600
```
monitor /var/log/fail2ban.log

---

### Post by SchnappiJedi on 2016-07-16
> **Habitual said:**
> Your other thread perhaps, methinks.

Yes that was stupid. 

Still though Fail2ban isn't working properly (like it used to on Ubuntu 12 LTS) on Ubuntu 14 LTS. Banning for 600 seconds is not wanted. Yet Fail2ban works fine on Ubuntu 16.

Just tried to login over six times via SSH on Ubuntu 14 with:
bantime = 2592000
maxretry= 2
findtime = 86400

and no ban. IP is not on ignore list. There is something wrong in my humble opinion.

---

### Post by Habitual on 2016-07-16
> **SchnappiJedi said:**
> Yes that was stupid. Still though Fail2ban isn't working properly (like it used to on Ubuntu 12 LTS) on Ubuntu 14 LTS. Banning for 600 seconds is not wanted. Yet Fail2ban works fine on Ubuntu 16.

Just tried to login over six times via SSH on Ubuntu 14 with:
bantime = 2592000
maxretry= 2
findtime = 86400

and no ban. IP is not on ignore list. There is something wrong in my humble opinion.
the ssh jail works out of the box with very little "editing" required.

Well, hang out. Some else may be along to help.

Good Luck.

---

