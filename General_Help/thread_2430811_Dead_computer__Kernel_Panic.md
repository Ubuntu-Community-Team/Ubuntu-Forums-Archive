---
title: "Dead computer : Kernel Panic?"
date: 2019-11-07
forum: General Help
---

### Post by Rrory on 2019-11-07
I have a 5 year old Toshiba that I had installed Ubuntu 18.04 on. Everything was great and one day it just died. no power light. I'm a long-term user but no tech-type so I looked around and found I should try blasting some air. Well and good it powered up then I saw "kernel panic"  and it died, died died.  No power light.
can this computer be revived or should I just bury my longtime trusty Toshiba?
Rory

---

### Post by Bashing-om on 2019-11-07
Rrory; Hello-

With the info provided all we can do presently is poke and stroke.
is the power source stable (flakey surge protector) ?
Internal Power supply unit failing ?- overheating ?
File system corrupted ?
Hard drive died ?

What results when attempting to boot a LiveUSB ?

[INDENT][INDENT]welcome to the art of troubleshooting
[/INDENT][/INDENT]

---

### Post by tux-peng on 2019-11-07
Can you remove the battery for a few minutes?

---

### Post by guiverc on 2019-11-07
Myself I'd open up the box, and start checking the PSU (power supply unit) gives correct voltages, the Power-Good signal is high (and not remaining low) etc, then move to look at motherboard etc...   ie. reading your description made me think your hardware needs checking  (which also means checking the power cable is securely connected & hasn't been knocked loose etc).

I wouldn't worry about kernel panic myself; since it was powered-off (died) without being cleanly shutdown; I usually boot a 'live' media (eg. Ubuntu install media) and `fsck` the partitions before i start to explore if the kernel panic is related to a concern...

---

