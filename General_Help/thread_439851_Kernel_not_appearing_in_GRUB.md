---
title: "Kernel not appearing in GRUB"
date: 2007-05-11
forum: General Help
---

### Post by maldek on 2007-05-11
I decided I'd try out the K7 kernel to see if it was able to get more speed out of my Athlon FX-55 so I installed the kernel using ```
sudo apt-get install linux-k7
```

The problem is, when I reboot, I still only have the 386 kernel to pick from in GRUB.  What's the deal?

---

### Post by mcduck on 2007-05-11
What version of Ubuntu are you running? In Edgy (6.06) and Feisty (7.04) there is no more separate optimized kernels for K7 and 686, instead the Generic kernel will recognize your CPU at boot time and then enable correct optimizations automatically.

So, if you are running one of those, get the linux-generic instead.

---

### Post by maldek on 2007-05-11
Ah, I'm using Feisty.  So I guess this is about as fast as I'm going to get. Thank you.

---

### Post by mcduck on 2007-05-11
> **maldek said:**
> Ah, I'm using Feisty.  So I guess this is about as fast as I'm going to get. Thank you.
well, if you are really running the 386 kernel, get the generic one instead.

---

