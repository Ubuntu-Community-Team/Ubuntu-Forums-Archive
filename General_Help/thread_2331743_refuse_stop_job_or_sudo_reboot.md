---
title: "refuse stop job or sudo reboot?"
date: 2016-07-25
forum: General Help
---

### Post by oui on 2016-07-25
Sometimes Lubuntu ends/restarts with a Stop job, often 90 s. This can be very bad if you are already in the hurry (as all pc activities can be longer as you really have time to do them :( !).

How to avoid it?

Refuse the stop job (for ex. with a key combination like Ctrl C) or never use the menu if in hurry and prefer sudo reboot to close all the opened / mounted devices?

---

### Post by ajgreeny on 2016-07-25
> Sometimes Lubuntu ends/restarts with a Stop job, often 90 s.

I don't know exactly what you mean by the above statement.
What sort of jobs do you sometimes need to stop?

Tell us a lot more and we may be able to help you.

---

### Post by mc4man on 2016-07-25
90 sec is clearly too long. Plus in all the times that happens here nothing positive happens during those 90 sec.'s, ie. the hanging stop job never resolves, it just times out.
Here, using an ssd so expect quick shutdowns or restarts,  I've lowered the timeout for this to 10 sec. This is configured here - 
/etc/systemd/system.conf

The line, at least for the stop jobs affecting me, is #DefaultTimeoutStopSec=90s (- line 35, see screenshot), so I edit to 
DefaultTimeoutStopSec=10s  (- note the # is also removed

---

### Post by ajgreeny on 2016-07-25
OK; looks as if this is part of systemd according to mc4man's post, so there I will leave you in the hands of someone who knows more than I do about systemd, as I'm still using 14.04 except in Virtual installs of 16.04 using VBox.

---

