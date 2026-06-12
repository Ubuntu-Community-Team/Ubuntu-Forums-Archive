---
title: "Will I need to do anything special for processor upgrade? (AMD XP to AMD X2)"
date: 2008-01-11
forum: General Help
---

### Post by jamesey on 2008-01-11
In Windows, when one upgrades from an AMD XP processor to an AMD dual core X2 processor, one has to install some special drivers, otherwise Windows will only use one of the cores.

In Ubuntu, if I upgrade from an AMD 3000 XP to an AMD 3800 X2, will it automatically be recognized? Is there a dual processor command I'll need to enable in Ubuntu?

---

### Post by EndPerform on 2008-01-11
I believe the kernel by default has SMP support built in, so you shouldn't need to do anything.

---

### Post by chewearn on 2008-01-11
> **jamesey said:**
> In Windows, when one upgrades from an AMD XP processor to an AMD dual core X2 processor, one has to install some special drivers, otherwise Windows will only use one of the cores.

In Ubuntu, if I upgrade from an AMD 3000 XP to an AMD 3800 X2, will it automatically be recognized? Is there a dual processor command I'll need to enable in Ubuntu?


I reckon there is no need, since the CPU is handled by the linux kernel.  The default ubuntu kernel is already compiled with SMP support, so the dual core AMD X2 should be automatically supported.

However, if I'm not mistaken, AMD XP is 32-bit processor, which means you are currently running i386 32-bit ubuntu.

The AMD X2 is 64-bit; while it is perfectly ok to continue to use 32-bit ubuntu in AMD X2, you might want to look towards 64-bit ubuntu in the future.

---

### Post by dcstar on 2008-01-12
> **jamesey said:**
> In Windows, when one upgrades from an AMD XP processor to an AMD dual core X2 processor, one has to install some special drivers, otherwise Windows will only use one of the cores.

In Ubuntu, if I upgrade from an AMD 3000 XP to an AMD 3800 X2, will it automatically be recognized? Is there a dual processor command I'll need to enable in Ubuntu?

If you have a Brisbane core X2 then you can kiss any accurate CPU core diode temperature monitoring goodbye.....     :-( (hint: add a 20C offset and it becomes reasonably close).

Anyhow, Ubuntu will just start working (at least) twice as well automagically!

---

