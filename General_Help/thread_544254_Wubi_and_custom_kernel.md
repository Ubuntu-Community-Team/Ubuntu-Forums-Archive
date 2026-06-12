---
title: "Wubi and custom kernel"
date: 2007-09-06
forum: General Help
---

### Post by moulin on 2007-09-06
Since Wubi uses the generic kernel I tried to install a 686 kernel. With a normal installation it will be added to grub automatically. First of all, is it possible to adjust the kernel in Wubi/grub4dos? Secondly, how different is the  kernel installed by Wubi different from the normal installation? 

Kind regards,

Marco

---

### Post by ago on 2007-09-06
> **moulin said:**
> Since Wubi uses the generic kernel I tried to install a 686 kernel. With a normal installation it will be added to grub automatically. First of all, is it possible to adjust the kernel in Wubi/grub4dos? Secondly, how different is the  kernel installed by Wubi different from the normal installation? 

Kind regards,

Marco

When you install a new kernel, that one will be used by default, it is added to menu.lst in wubi/boot

---

### Post by moulin on 2007-09-06
Ah! I tried to install linux-kernel-686-smp but now I read in Synaptic it is obsoleted by linux-image-generic :-) Thank you for your answer.

---

