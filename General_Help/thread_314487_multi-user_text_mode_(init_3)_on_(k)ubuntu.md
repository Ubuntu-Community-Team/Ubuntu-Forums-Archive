---
title: "multi-user text mode (init 3) on (k)ubuntu"
date: 2006-12-07
forum: General Help
---

### Post by PgR on 2006-12-07
I learnt linux with Mandrake....

If I wanted to stop X (eg, to install new graphic card driver) then it was "init 3" That gives multi-user text-only mode.

In Ubuntu it seems that init 2 up to init 5 is the full graphic works. I can get to single user by rebooting to it; and I know I can stop the X-server to install the graphic card drivers... so I guess the question is...

How to I get to "runlevel 3" (multi-user text-only type mode) in Ubuntu? And how can I change runlevel without rebooting (come on, this isn't windows!) ](*,) 

[kubuntu 6.10 on AMD64]

---

### Post by dcstar on 2006-12-07
> **PgR said:**
> I learnt linux with Mandrake....

If I wanted to stop X (eg, to install new graphic card driver) then it was "init 3" That gives multi-user text-only mode.

In Ubuntu it seems that init 2 up to init 5 is the full graphic works. I can get to single user by rebooting to it; and I know I can stop the X-server to install the graphic card drivers... so I guess the question is...

How to I get to "runlevel 3" (multi-user text-only type mode) in Ubuntu? And how can I change runlevel without rebooting (come on, this isn't windows!) ](*,) 

[kubuntu 6.10 on AMD64]

Easiest thing would probably be to switch to a text screen (CTRL-ALT-F1), log in and then stop the GDM service.

---

### Post by PgR on 2006-12-08
That would do it; thanks.

---

