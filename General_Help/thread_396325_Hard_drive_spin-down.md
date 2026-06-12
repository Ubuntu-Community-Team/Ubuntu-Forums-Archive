---
title: "Hard drive spin-down"
date: 2007-03-29
forum: General Help
---

### Post by Orange Crush on 2007-03-29
Quick question:

I'm running Kubuntu x64 Edgy, and I have a few extra (and noisy) drives in my machine that I'd like to spin down when idle.  I can set this easily enough with hdparm at the command line after booting, but I'd like the setting to "stick" between reboots.  What's the "correct" way of setting this?  I poked around in the man page and /etc/init.d/hdparm but haven't made much sense of it.

Thanks!

---

### Post by dcstar on 2007-03-29
> **Orange Crush said:**
> Quick question:

I'm running Kubuntu x64 Edgy, and I have a few extra (and noisy) drives in my machine that I'd like to spin down when idle.  I can set this easily enough with hdparm at the command line after booting, but I'd like the setting to "stick" between reboots.  What's the "correct" way of setting this?  I poked around in the man page and /etc/init.d/hdparm but haven't made much sense of it.

Thanks!

Edit /etc/hdparm.conf

---

