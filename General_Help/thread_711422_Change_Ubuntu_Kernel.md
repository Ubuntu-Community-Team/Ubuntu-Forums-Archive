---
title: "Change Ubuntu Kernel?"
date: 2008-02-29
forum: General Help
---

### Post by cebert85 on 2008-02-29
Hi, I am fairly new to Ubuntu and was wondering if there is any performance gane by compiling your own ubuntu kernel.

I have an AMD 3400, running in 32 bit mode.

when I run uname -a
I am using the 2.6.22-14-generic i686 kernel, which from reading on these forums is the fastest generic kernel you can use?

Would I really notice any performance differences by compiling my own kernel?

---

### Post by Archmage on 2008-02-29
> **cebert85 said:**
> Would I really notice any performance differences by compiling my own kernel?

Roughly you could gain 0,01% better performance. I let this up to you to decide if you notice this and if it would be worth the cost (a newbie would need a few hours to build there own kernel a few days to learn what he needs and don't needs in the kernel.)

---

### Post by pointone on 2008-02-29
You might speed up the boot process by eliminating unnecessary modules/drivers, but as Archmage says, the performance benefits are fairly marginal. Most people build custom kernels for other reasons.

---

### Post by msarro on 2008-02-29
It used to be that you would get a substantial gain in performance from compling your own, but honestly, its not worth it these days. A ton of advances have come and been implemented, and the performance gain you get is so minimal at this point its absolutely not worth it in my opinion. If you really want to do it, go for it, its a good learning experience. But by no means is compiling your own kernel necessary, or even desirable in most situations these days (unless you're coming from gentoo world).

---

