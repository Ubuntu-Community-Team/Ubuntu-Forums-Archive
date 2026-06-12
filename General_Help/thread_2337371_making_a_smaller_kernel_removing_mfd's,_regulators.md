---
title: "making a smaller kernel: removing mfd's, regulators, i2c and led support?"
date: 2016-09-17
forum: General Help
---

### Post by bartgrefte on 2016-09-17
A while ago I started looking into how to recompile the kernel, initially because it didn't came with support for DFS in the Atheros drivers, for some reason that particular option is disabled.

Then I started looking into what could be removed from the kernel (mainly to make the compiling go a whole lot faster) after which I managed to get rid of quite a bit of unnecessary drivers.

Unfortunately, at some point I ran into drivers that I do not know if it's safe to remove those. For example:
- CONFIG_MFD_* , I can't tell if MFD's are found on consumer motherboards, server boards, embedded systems or exclusively in external hardware;
- The same with CONFIG_REGULATOR_*
- CONFIG_I2C_*
- And CONFIG_LEDS_* With these I'm also wondering if those are required for controlling the power-, hdd- and nic-led's or are these meant for something else (as well)?

Are there any ways to tell which options (don't) apply to consumer motherboards?

---

### Post by DuckHook on 2016-09-17
AFAIK, the only way to find MOBO components is to read the MOBO specs (the actual design specs, not the consumer spec summary that is part of most User Guides).

I've only compiled a few kernels in my computing life, so take my words for the rank amateurism that they actually are, but my understanding is that one can choose to either compile drivers into the kernel itself, or have them load automatically at boot. If choosing the latter, the driver can be blacklisted. Doing this selectively through a process of trial and error should tell you which are system-critical and which are not.

---

