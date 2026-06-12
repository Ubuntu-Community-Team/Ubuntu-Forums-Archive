---
title: "two different &quot;restricted modules&quot; versions?"
date: 2007-02-15
forum: General Help
---

### Post by ghira on 2007-02-15
I've used RedHat/Fedora for 6+ years, but I'm new to Ubuntu.

My system is offering me both "linux-restricted-modules" version
2.6.15.26 and "linux-restricted-modules-2.6.15-28" as updates.

Also, "linux-386" version 2.6.15.26 and "linux-image-2.6.15-28"

Likewise dual versions of headers. 

Have I uncommented too much stuff in the file synaptic and apt-get and so
on use for config? Or is this all perfectly normal?

I'm aware I'll need to re-run the nvidia script after a kernel upgrade.

---

### Post by fragos on 2007-02-15
The image you boot will use the matching restricted modules package.  To remove the older version, go to Synaptic and remove completely the unwanted image version.  This will delete the matching restricted and edit menu.lst to update grub.  Boots will no longer ofer the removed kernel version.

---

### Post by ghira on 2007-02-16
Thanks. Why does Synaptic seem to want to install  both, rather than just the most recent one? When yum has seen multiple kernel upgrades in the past it's only offered me the newest one, iirc.

---

### Post by fotakis on 2007-02-16
> **ghira said:**
> Thanks. Why does Synaptic seem to want to install  both, rather than just the most recent one? When yum has seen multiple kernel upgrades in the past it's only offered me the newest one, iirc.
Because you might want to boot from the other kernel at some point IMHO.

---

### Post by ghira on 2007-02-17
OK. Well, it's worked fine (here I am). So I'll be less concerened in future.

---

