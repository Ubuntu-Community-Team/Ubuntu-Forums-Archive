---
title: "System tray - something keeps crashing"
date: 2007-02-10
forum: General Help
---

### Post by kairu0 on 2007-02-10
For the past week or so, every time that I restart I get an icon in the system tray that says something to the effect of "a service/application has crashed," althouhg I'm not using an English locale so I don't know verbatim.

When I click on it, it disappears and nothing comes up.

How can I found out what is crashing?

---

### Post by Maestro23 on 2007-02-10
Log files are kept in [COLOR="Red"]/var/log[/COLOR].  

Take a peek in there.

---

### Post by kairu0 on 2007-02-11
Turns out that upgrading to kernel 2.6.11 fixed the problem.

---

