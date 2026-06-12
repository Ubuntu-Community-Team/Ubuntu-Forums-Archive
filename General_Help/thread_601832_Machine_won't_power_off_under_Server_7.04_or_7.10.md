---
title: "Machine won't power off under Server 7.04 or 7.10"
date: 2007-11-03
forum: General Help
---

### Post by jamoo1980 on 2007-11-03
Hello all

I've installed Ubuntu Server Edition, and everything seems to be just fine except that I can't shut the system down without holiding down the power button. When I do

```
sudo shutdown -h now
```

...everything goes according to plan; the system halts, but doesn't actually power off the motherboard. I've tried server edition 7.10 and 7.04, both with exactly the same results.

The strange thing is, when I boot from an Ubuntu DESKTOP edition (7.04) and shutdown from within Gnome, the system shuts down and the motherboard powers off! So, I've ruled out hardware trouble. I'm assuming that the desktop edition must have some component installed, or enabled, that the server edition doesn't, and that this is causing the server edition not to power off the motherboard.

Having looked at similar posts, I have tried adding acpi=force to the grub script, to no avail. I then tried adding apm to /etc/modules, and this hung the system on boot.

So, any other ideas what I can do to resolve this problem? The motherboard is clearly capable of being powered off by the operating system, so what am I missing?

Any help greatly appreciated!

Thanks :)
James

---

### Post by dcstar on 2007-11-03
> **jamoo1980 said:**
> Hello all

I've installed Ubuntu Server Edition, and everything seems to be just fine except that I can't shut the system down without holiding down the power button. When I do

```
sudo shutdown -h now
```

...everything goes according to plan; the system halts, but doesn't actually power off the motherboard. I've tried server edition 7.10 and 7.04, both with exactly the same results.

The strange thing is, when I boot from an Ubuntu DESKTOP edition (7.04) and shutdown from within Gnome, the system shuts down and the motherboard powers off! So, I've ruled out hardware trouble. I'm assuming that the desktop edition must have some component installed, or enabled, that the server edition doesn't, and that this is causing the server edition not to power off the motherboard.

Having looked at similar posts, I have tried adding acpi=force to the grub script, to no avail. I then tried adding apm to /etc/modules, and this hung the system on boot.

So, any other ideas what I can do to resolve this problem? The motherboard is clearly capable of being powered off by the operating system, so what am I missing?

Any help greatly appreciated!

Thanks :)
James

Check which kernels are being loaded - there may be an updated/different one that works.

---

### Post by jamoo1980 on 2008-01-26
I'm finally getting round to returning to this problem (see my post above). The kernel I'm running is 2.6.22-14-server. I still can't get the system to power off, although I know the motherboard supports it (works with Desktop edition of Ubuntu). Any ideas???

Many thanks :)
James

---

### Post by jamoo1980 on 2008-01-27
No-one?

Well, the plot thickens... My machine will shutdown and power off if booted from an Ubuntu 7.10 Live CD. It will shutdown and power off if booted under Debian server 4.0. It won't shutdown and power off under Ubuntu server 7.10 or 7.04.

Given the above I'm convinced this is not a hardware or firmware problem, but a configuration problem of some sort.

At the moment my alternatives are switching to Debian, or to an earlier version of Ubuntu (poss. 6.06) but I'm reluctant to do this as it leaves a problem unresolved... Any ideas?

Cheers
James

---

