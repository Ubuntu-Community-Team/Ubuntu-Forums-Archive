---
title: "Marvell Gigabit (Newbie)"
date: 2005-10-31
forum: General Help
---

### Post by pbb on 2005-10-31
Hi all !

I really am a newbie, just recently started trying out Linux. I am trying out the Ubuntu Live CD at the moment, and have one main problem.

I am trying to activate my Marvell (Yukon) Gigabit LAN card, which is not detected by default by Ubuntu.
Searching internet, I've discovered I either need to use /lib/modules/2.6.12-9-386/kernel/drivers/net/sk98lin/sk98lin.ko, or install the driver from [http://www.syskonnect.com/syskonnect/support/driver/htm/sk9elin.htm](http://www.syskonnect.com/syskonnect/support/driver/htm/sk9elin.htm)

However, I have no idea how to enable a driver from a .ko file, and the driver from syskonnect needs header source files for installation. I've installed the packages "linux-headers-2.6.12-9" and "linux-kernel-headers", but these did not seem to be the ones needed.

Can someone guide me further? I really am a newbie in this, so step-by-step help would be greatly appreciated.

Thanks, Peter

---

### Post by pbb on 2005-11-01
Can really nobody help me ?

---

### Post by riggsd on 2005-11-01
The module should already be there, load it like this.

```
sudo modprobe sk98lin
```

---

