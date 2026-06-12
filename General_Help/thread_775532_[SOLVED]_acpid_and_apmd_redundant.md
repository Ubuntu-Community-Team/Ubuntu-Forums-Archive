---
title: "[SOLVED] acpid and apmd redundant?"
date: 2008-04-30
forum: General Help
---

### Post by ethanay on 2008-04-30
my understanding is that acpi is meant to replace apmd.

i am running 8.04 on a fairly new dell xps m1330, and under system > administration > services both acpid and apmd are enabled by default.  is this correct, or can/should i disable apmd?

thanks,
ethan

UPDATE: I have disabled the apmd via system > administration > services and still have full hibernate/suspend functionality.  I am leaving acpid running.

---

### Post by astadolfo3 on 2008-05-08
Hi Ethan,

if you PC is recent you can try to disable the apmd service since it's used only in motherborads made before 2000. In case you get some issues you can always re-enable it from service settings menu.

If you disable apmd on the service settings and everything works fine using only acpid, you can remove the apmd package with synaptic.

hope this helps!

---

### Post by ethanay on 2008-05-08
yes, it does, thank you!  I understand for compatibility why it still exists -- but for a default install I think it is a bit overwhelming to include apm, acpi, and pm-utils all.  When all are enabled by default, it implies to me, "These have separate functions so don't disable unless you want to screw something up."  However, then I read others' writing that pm-utils replaces acpi replaces apm, and it just leaves me confused.

---

### Post by 4Orbs on 2008-09-02
Does this also mean that, because I have an old desktop, I can safely disable or uninstall acpid?

---

### Post by ethanay on 2008-09-22
i believe so -- you can try it, since it won't hurt anything.  just uncheck the box in the administration > services (or sessions, i forget which).  if it messes something up, recheck the box.  if all is well, you can uninstall completely.

---

### Post by freqmode on 2008-09-23
Brilliant. I was having all kinds of sleep and hibernate issues where the system would freeze before powering off. I diabled apmd and the problem seems to be fixed. Thanks for the suggestion!

---

### Post by kkathman on 2008-11-13
If you are operating a desktop, always plugged in, do you actually need either one?

---

