---
title: "Sleep and Hibernate fail to activate devices 00:07 and 00:08"
date: 2007-01-23
forum: General Help
---

### Post by craz on 2007-01-23
Hi.  I have a problem with sleep and hibernate on my computer.  I know many people have had problems but even with the many posts I cannot figure out a fix for my problem.  So if you could help, I would REALLY appreciate it.  Really I mean it.

When I try to sleep or hibernate I get the error message:
```
pnp: failed to activate device 00:07
pnp: failed to activate device 00:08
```

Then I just get a black screen.
I tried using lspci in the terminal, but these devices do not show up - not many do.

What is the first step I should take?

---

### Post by craz on 2007-01-24
Any ideas?
Thanks.

---

### Post by freshmint on 2007-01-25
im getting the same message, but mine also says something about not having enough swap.

---

### Post by craz on 2007-01-25
You might have to increase the partition size of you linux swap partition.  For the error messages about devices, I have no idea what to do :/

---

