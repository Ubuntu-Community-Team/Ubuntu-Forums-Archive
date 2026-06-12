---
title: "Ubuntu booting error - Kernel Panic : not syncing"
date: 2007-11-17
forum: General Help
---

### Post by sc2 on 2007-11-17
Kernel panic - not syncing is the last line I see when running gutsy in recovery mode. Help?

---

### Post by Arwen on 2007-11-17
In my case (when I had installed ubuntu 5.10) it was bad RAM..

---

### Post by sc2 on 2007-11-17
> **Arwen said:**
> In my case (when I had installed ubuntu 5.10) it was bad RAM..



I'm running the Vista partition on here just fine right now. It (gutsy) was working last night.


Here's the actual error, though:

```

Kernel Panic - Not syncing: no init found try passing init=opt ion to kernel

```

I'm think opt ion is option but it got cut off.. o_O

---

### Post by sc2 on 2007-11-17
Bump.. :x

---

### Post by confused57 on 2007-11-17
You could try adding init=option to the kernel line in the grub boot menu...you can do this by highlighting your Ubuntu entry, press "e", highlight your kernel line, press "e" again, add the init=option to the end of the kernel line, press "enter", then "b" to boot.  This change is only temporary, but you can check if it works.

Did you do any partitioning or change anything in Gutsy just before the problem started?

---

