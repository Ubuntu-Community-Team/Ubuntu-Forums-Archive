---
title: "Can't reboot: Upstart kills rc6!"
date: 2008-05-07
forum: General Help
---

### Post by Designer on 2008-05-07
The subject says it al: when i type 'reboot' or 'shutdown' nothing happens. (except for the messages and the runlevel is changed to 6)

But then Ubuntu just sits there...and i have to power off manualy to reboot.

When i checked my logs i noticed this:

May  7 15:52:42 xchange init: rc6 main process (17554) killed by TERM signal

This means that rc6.d never is called..

Anyone please?

Dirk

---

