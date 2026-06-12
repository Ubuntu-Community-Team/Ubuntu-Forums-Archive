---
title: "Random boot"
date: 2013-12-14
forum: General Help
---

### Post by Guillaume_F. on 2013-12-14
I own a VPS and I installed ubuntu on it but since like a couple weeks I get random boot message in console via putty

Broadcast message from root@bighouse
        (unknown) at 1:11 ...


The system is going down for halt NOW!


I don't know what cause it what is the general way to "debug" such situation

thank you.

edit:  I did a tail -50 on /var/log/message the last messages are

Dec 15 01:12:11 bighouse exiting on signal 15
Dec 15 01:13:32 bighouse syslogd 1.5.0#6ubuntu1: restart.

---

### Post by tgalati4 on 2013-12-14
Here's a Haiku:

Is "Own" correct here?
Your server gets shut down, but
You didn't do it.

Signal 15 is simply a terminate flag that was sent to a process (probably *init*, the mother of all processes), so the system goes down.  Perhaps the hosting service is having problems?

---

