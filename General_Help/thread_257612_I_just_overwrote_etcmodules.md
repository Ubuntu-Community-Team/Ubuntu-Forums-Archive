---
title: "I just overwrote /etc/modules"
date: 2006-09-14
forum: General Help
---

### Post by chenel on 2006-09-14
So I just overwrote /etc/modules (I typed in "echo ___ > /etc/modules" rather than "echo ___ >> /etc/modules").  Is there any way to regenerate and/or recover it?

I am abroad right now, and have a laptop, and don't have either (a) an ubuntu CD or (b) a way of burning one at the moment.

Help!

-chenel

---

### Post by kaens on 2006-09-14
Can you boot, or is the machine currently running?

Also, do you remember what was in the file?

---

### Post by chenel on 2006-09-15
The machine is currently running - I was afriad to shut down.

---

### Post by yopnono on 2006-09-15
/etc/modules ? are you talking about lib/modules. If so just install the kernel.

EDIT:
Sorry i was thinking about the folder.

here is my modules content:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
```

---

### Post by chenel on 2006-09-15
Thanks for the input...

Does anybody reading this happen to have a Dell Inspiron notebook?  Mine's an old 8100 and I'd like to know if there are extra modules that were auto-detected by the ubuntu installer (for little things like my ethernet card, etc.) that I'll still be missing...

---

### Post by chenel on 2006-09-15
Ooh, just had an idea.

If I do ```
lsmod
``` will that list all of the modules that I need to put back in, since the system is still running?

---

### Post by yopnono on 2006-09-15
> **chenel said:**
> Thanks for the input...

Does anybody reading this happen to have a Dell Inspiron notebook?  Mine's an old 8100 and I'd like to know if there are extra modules that were auto-detected by the ubuntu installer (for little things like my ethernet card, etc.) that I'll still be missing...

Closest I get is a dell d610 Thats my entry from

---

### Post by mitch.c on 2006-09-15
> **chenel said:**
> Ooh, just had an idea.

If I do ```
lsmod
``` will that list all of the modules that I need to put back in, since the system is still running?

I don't think that would hurt... worst that will happen is you'll get a message about trying to load a module that's already loaded.

Could you lsmod while the machine is still running, and then lsmod after a reboot and compare the differences? Just put the differences in /etc/modules.

---

### Post by chenel on 2006-09-15
Good call.  I'll give it a shot.

Thanks.

---

### Post by chenel on 2006-09-15
Well, I put lp and psmouse in /etc/modules, restarted, and everything seems to work still, so here's hoping it's fixed.

Thanks everybody!

---

