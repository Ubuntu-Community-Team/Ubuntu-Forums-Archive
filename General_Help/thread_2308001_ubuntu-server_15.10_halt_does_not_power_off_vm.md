---
title: "ubuntu-server 15.10 halt does not power off vm"
date: 2015-12-30
forum: General Help
---

### Post by Franz_Schindler on 2015-12-30
Hello,

if i use halt the vm stay's in the "System is halted" message.
If i use halt -p the vm really powers off?

I this a bug or a feature?

Kind Regards
/Franz

---

### Post by DuckHook on 2015-12-30
Hi Franz,

Halt does not power off. It just brings system to halt state. Whether halt is equivalent to power off depends on your system's BIOS. They are all different and treat the command differently. On the machines I tinker with, about half will proceed to poweroff, and half will just halt (with power still on).

To truly get to power off every time, use```
poweroff
```To reboot, use```
reboot
```Aside from being convenient, they are clearer commands that do what they say.

---

