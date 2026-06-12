---
title: "Some questions about kernel"
date: 2007-05-26
forum: General Help
---

### Post by chunchengch on 2007-05-26
1. The kernel version of my Ubuntustudio is 2.6.20-15.27, however, I find a newer version 2.6.20-16.28 in the Synaptic, what is the difference between? and is it necessary to upgrade?

2. I heard that in order to optimize the performance of computer, it is better to install the kernel according to CPU, generic is not the appropriate one, is it correct? for example, I have a Intel Core Dual T2250 CPU, so I should install linux-image-2.6.20-15-386 instaed of linux-image-2.6.20-15-generic, am I right?

3. If the answer of question 2 is "yes", how should I do to switch to the "right" kernel?

4. I spent a lot of time and efforts to install various applications, will these applications malfunction after upgrade or switch of the kernel?

---

### Post by energiya on 2007-05-28
1. Only if it adds support/adds better support for hardware that you have, it fixes a major bug or the old one just doesn't run wright for you.

2. For a dual core the generic one should be better, I think. The best thing to do would be to recompile the kernel, but that needs you to know your hardware (and know a little about computers)

3. *

4. Only the ones that need a module atached to the kernel, like the nVidia drivers, lm_sensors and other (usually drivers and applications that need low level acces)

---

