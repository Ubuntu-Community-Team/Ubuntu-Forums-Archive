---
title: "[SOLVED] Help with BRAND NEW pc/all versions fail"
date: 2007-12-14
forum: General Help
---

### Post by Ripfox on 2007-12-14
Hi people, whats up. Well I just bought a motherboard/processor combo today along with a new case and some ram ect...it's not great but it's better than what I had left at my current state financially. AMD 3400+ Sempron 1.8ghz on a Gigabyte S-series motherboard (ga-m61sme-s2)

Also got a 160 gig SATA hdd, and I have tried every Ubuntu cd I have in the HOUSE  on this rig to no avail!! One error after another, bonobo activation error, nautilus crash error, on the alternate Gutsy cd, the grub bootloader fails to install...what the heck I have NEVER had this many errors on any computer with Ubuntu. The only thing I can think of is that I am using an older cdrw but that can't be it b/c I've installed successfully with this drive on older rigs. Is this a problem with SATA type hdd drives? Any help at all is appreciated.

Rip

---

### Post by Craigus on 2007-12-14
Have you run memtest86+  ?

---

### Post by Ripfox on 2007-12-14
Sorry can you elaborate?

---

### Post by Craigus on 2007-12-14
memtest86+ is a RAM testing program and can be run from the live CD (the test memory option). New RAM is sometimes faulty. Flaky performance can be due to faulty RAM.

---

### Post by Ripfox on 2007-12-14
Cool. But I ran it and no errors. Bah! I am taking it back today and getting all the components replaced.

Just out of curiosity, has there been any problems with newer SATA drives and Ubuntu?

---

### Post by xeth_delta on 2007-12-14
I am not sure I understand the problem you have. Is all this happening after installation?

---

### Post by Ripfox on 2007-12-14
During, after, one time it installed gutsy all the way then during updating it stalled on restarting cupsys, then the machine crashed...so yea, all of the above.

---

### Post by Ripfox on 2007-12-14
Tried Feisty, it will boot to the desktop then freeze...no panel. Sometimes nautilus will crash too.

---

### Post by xeth_delta on 2007-12-14
Can you please post the output from running dmesg in the terminal? It might indeed be also a hardware issue. Can you check te temperature of your CPU?

---

### Post by Het Irv on 2007-12-14
dumb question but you do have a heatsink thermal paste for your processor.  If the error does not seem to have a pattern I could be an overheating problem

---

### Post by psusi on 2007-12-14
How long did you let memtest86 run for?

---

### Post by Ripfox on 2007-12-15
Eh, I took the whole thing back and got a 4200 AMD Dual Core instead of the Sempron. Brought it home and Gutsy installed fine and dandy. Ghost in the machine I guess.

(I ran it overnight)

---

### Post by xeth_delta on 2007-12-15
> **ripfox said:**
> Eh, I took the whole thing back and got a 4200 AMD Dual Core instead of the Sempron. Brought it home and Gutsy installed fine and dandy. Ghost in the machine I guess.

(I ran it overnight)

Good to know it's working now! Can you please mark the thread as solved?

Xeth

---

### Post by Ripfox on 2007-12-15
Done...thanks for the reminder.

---

