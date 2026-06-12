---
title: "IgnoreIP seems to be getting ignored!  Fail2ban problem"
date: 2017-09-04
forum: General Help
---

### Post by Andrew_Benjamin on 2017-09-04
I have a VPS running at woothosting.  It has Ubuntu 16.04 installed. It is set up with a mail package called iRedMail which seems to be performing nicely.
The system installs fail2ban and configures 8 jails, one of which is sshd.  My home IP keeps getting banned, and I don't know why.

I gained access to the system via the emergency control panel at woothosting and 'unjailed' my home ip:
fail2ban-client set sshd unbanip MYIP

I then checked my /etc/fail2ban/jail.conf file.
As expected, it contained the line (set up previously):

ignoreip = 127.0.0.1/8 MYIP
where MYIP was the house IP.  The Ignoreip line is the first, non-comment in the [DEFAULT] section.  No other instance of ignoreip is in this file (ie no overriding dupe)

So, now being unbanned, I logged out and logged in via putty.  In putty, I intentionally mistyped the password several times and - banned myself.

Am I missing how ignoreip is supposed to work, or should I look somewhere else to put ignoreip?

Help?


Andrew

---

