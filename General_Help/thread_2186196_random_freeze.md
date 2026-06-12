---
title: "random freeze"
date: 2013-11-06
forum: General Help
---

### Post by scereze on 2013-11-06
Hi all,

Recently, my laptop (ubuntu precise) starts to freeze randomly. I can only stop it using the power button.
I would like to find what could be the cause of this recent behavior.
Question: once I restart my laptop, where should I look in order to find a trace/log of what happened?

thanks for your help.

Baocrazy.

---

### Post by inclusivedisjunction on 2013-11-07
It's possible relevant data would appear in an older dmesg log (/var/log/dmesg.0, for instance). You'll want to try to synchronize your file system next time it freezes, though. Press Ctrl-Alt-SysRq, release SysRq, and[ press R, E, I, S, U and then B]("http://en.wikipedia.org/wiki/Magic_SysRq_key#Uses"). That should synchronize your file systems and reboot.

---

### Post by mastablasta on 2013-11-07
freeze is often caused by overheating (usually GPU as otherwise it would do a reboot by itself). another option is bad capacitors issue.

---

