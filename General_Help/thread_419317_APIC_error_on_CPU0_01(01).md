---
title: "APIC error on CPU0: 01(01)"
date: 2007-04-22
forum: General Help
---

### Post by manifoldronin on 2007-04-22
Hi,

I just converted an old one from Win XP to Feisty. It's an Athlon 1800 on MSI motherboard. Everything appears to be functioning fine, except I'm getting the error message "APIC error on CPU0: 01(01)" in syslog, kern.log, and debug every couple of seconds!  I tried adding "noapic" to the boot options, but that didn't seem to have any effect.

Any thoughts? Thanks.

---

### Post by dcstar on 2007-04-23
> **manifoldronin said:**
> Hi,

I just converted an old one from Win XP to Feisty. It's an Athlon 1800 on MSI motherboard. Everything appears to be functioning fine, except I'm getting the error message "APIC error on CPU0: 01(01)" in syslog, kern.log, and debug every couple of seconds!  I tried adding "noapic" to the boot options, but that didn't seem to have any effect.

Any thoughts? Thanks.

I've seen similar things on Dual-CPU MBs with only one CPU installed, you might want to try a SMP kernel and see if that behaves better.

---

### Post by manifoldronin on 2007-04-23
Thanks for the reply.  The MB is a typical MSI board with VIA chipset from 2002. I don't think it actually supports dual-cpu. I also tried "nosmp" on boot options, but got all the same.

---

### Post by manifoldronin on 2007-04-24
I think I'm going to try building my own kernel, and see if I can disable apic at that point.

In fact, I don't really care about the errors themselves as most things seem to be working just fine. I'd be all happy if I could figure out a way to turn the error logging off so they won't flood all three log files.

---

### Post by manifoldronin on 2007-04-25
looks like klogd is the one who's been "spamming" - duh  - for now I think I'll just disable klogd.

---

