---
title: "laptop-mode enabled, not active . . . (????)"
date: 2012-11-02
forum: General Help
---

### Post by Farinet on 2012-11-02
lubuntu 12.10, Samsung 535 u3c (2xamd64)

Since 12.10 (with the change of the kernel from 3.2 to 3.5) i have big problems with suspend to ram and suspend to disk either. Also, the settings of what to do at <Close lid> seem to have absolutely no effect. There are similar problems in the ppc flavour as well (in x386 seems to work more or less correctely).

Now, searching for the reason of this problems i found something interesting in the syslog:

```
laptop-mode: Warning: Configuration file /etc/laptop-mode/conf.d/board-specific/*.conf is not readable, skipping.
```
Producing then, this result:
```
laptop-mode: enabled, not active
```

Now, that directory, i.e. /board-specific/ simply is inexisting on my computer. And i'm clueless what i could do to activate the laptop-mode (which, looking at the many scripts in the '/etc/laptop-mode/conf.d/' seems to be important for the control of power saving, suspending, locking screen etc.

Actually, i always have to suspend "by hand" (and even that was only possible after i installed - directly from the AMD website - their proprietarian fglrx driver (the built in driver worked fine, graphicswise, but in some way it seemed to have blocked completely suspend to ram. Suspend to disk worked, but shut down hardwarewise the wireless. This failure i "repaired" installing from launchpad the <samsung-tools>, which apparently were made for the Samsung netbooks, but which nevertheless give me control over some Fn-keys including the wireless related.

In any case, anyone out there who has an idea? TIA!! :)

---

