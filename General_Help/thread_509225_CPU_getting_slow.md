---
title: "CPU getting slow"
date: 2007-07-25
forum: General Help
---

### Post by beablis on 2007-07-25
Hi guys,

My CPU (AMD64 - 3000+) seems to be quite slow lately. I was able to compile MythTV in about 18min, now it takes 40 minutes. 
There appeared a BIOS error message for some time in the last few weeks: **System sensor: Failed ** but it doesn't appear anymore. 

Powernowd isn't working as reliable as before as well. When I start to compile something it stays at 1000MHz and sets the value high at 2000 only very rarely. 

Could you please check if you also see 4 times NO for this command:

```
 more /proc/acpi/processor/CPU0/info

Code:
processor id:            0
acpi id:                 0
bus mastering control:   no
power management:        no
throttling control:      no
limit interface:         no

```

I guess it must be wrong that everything is set to no there. What can be the reason?

---

### Post by blithen on 2007-07-25
How long have you had it for? The processor I mean.
We have the same chip by the way xP

---

### Post by beablis on 2007-07-26
Hi, I own the chip for about 2 years and I'm experiencing the slowdowns only recently. 

Could anyone please with a similar CPU (or even a different one with a powersaving feature) tell me the result of 

```
cat /proc/acpi/processor/CPU0/info
```

---

### Post by hessiess on 2007-07-26
dount use that cpu, but it could quite easely just be dust in the heatsink!

---

### Post by Tecguy2 on 2007-07-26
it could be overheating take the side off from your pc if it doesent help put a house fan straight at the pc

---

