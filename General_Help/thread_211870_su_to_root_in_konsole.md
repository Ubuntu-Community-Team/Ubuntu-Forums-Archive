---
title: "su to root in konsole"
date: 2006-07-09
forum: General Help
---

### Post by pgk3734 on 2006-07-09
When I su to root in a konsole I get:
configuration error - unknown item 'QUOTAS_ENAB' (notify administrator)
configuration error - unknown item 'NOLOGIN_STR' (notify administrator)
configuration error - unknown item 'ENV_HZ' (notify administrator)
configuration error - unknown item 'CHFN_AUTH' (notify administrator)
configuration error - unknown item 'CLOSE_SESSIONS' (notify administrator)
I'm trying to figure out why. This worked ok before and I think it happened
after trying to install antivirus program (yes, I know, not needed).
tia,
pgk:rolleyes:

---

### Post by aysiu on 2006-07-09
I don't know why you're *su*ing to root. Ubuntu doesn't enable the root account by default.

Typically you would preface each command with *sudo* or use ```
sudo -s
``` to get a root terminal.

That said, [this](http://www.linuxquestions.org/questions/showthread.php?s=&postid=1873845) may help your problem.

---

### Post by pgk3734 on 2006-07-09
Thanks for the linked tip. The article's info
solved the problem.
Much obliged.

---

