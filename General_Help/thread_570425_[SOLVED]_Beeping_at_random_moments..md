---
title: "[SOLVED] Beeping at random moments."
date: 2007-10-08
forum: General Help
---

### Post by MalfunctioningMartian on 2007-10-08
Does Ubuntu ever beep?
Every now and then my computer beeps for apparently no reason at all.

---

### Post by Nesman on 2007-10-08
I haven't found Ubuntu to beep, really.  There are a few things you might want to look at.  After a beep happens, check the last few lines of /var/log/syslog
It might also be helpful to run dmesg in terminal and see what the last few lines say there.

I had an issue where my computer would randomly make "boi-oi-oi-ng" and "uh-oh" noises.  It turned out that centericq (console based IM program) was set to play sounds on incoming messages and events.  The computer it used to be on didn't have speakers, and it runs in text mode, so I never suspected it.

---

### Post by MalfunctioningMartian on 2007-10-17
Turns out it was my IM program telling me I've got e-mail.

---

