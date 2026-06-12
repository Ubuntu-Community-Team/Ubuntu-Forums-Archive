---
title: "speed difference with i686 kernel?"
date: 2006-08-07
forum: General Help
---

### Post by skale on 2006-08-07
I have a Pentium 4, and have the 386 kernel. Will there be a noticeable speed difference with the i686 kernel worth the effort in recompilation? Will there be any difference at all? Opinions abound.

---

### Post by vijirajan on 2006-08-07
You would notice difference for CPU intensive tasks like Compiling and Video editing.

---

### Post by az on 2006-08-07
> **skale said:**
> Will there be a noticeable speed difference with the i686 kernel worth the effort in recompilation? 

You don't have to recompile the kernel.  Just install linux-686.  That will bring in all the 686 kernel packages and future updates.

Whether you notice a difference or not depends on what you do.  The 686 kernel does run faster since it is optimised for Pentium.

---

### Post by hopstah on 2006-08-07
what would be the kernel that is optimized for an amd64 (running 32 bit ubuntu)?  and is that kernel just as stable as the 386 branch?

---

### Post by canadianwriterman on 2006-08-07
I also have a Pentium 4 processor and I've tried the 686 kernel several times and have noticed a slight increase in speed. The main difference is in CPU usage. For example, using Limewire/Frostwire always spiked my CPU at 100% when using the standard 386 kernel. When I installed the 686 kernel, CPU usage dropped dramatically. However, I had a persistent problem with the 686 kernel... serveral times a day, the system would freeze (no response from any input and no CPU activity) requiring a complete reboot. It got to be such a pain, that I reverted back to the 386 kernel.

Now, my P4 is single core, with hyperthreading. The proper kernel to take advantage of HT is the 686-smp, but I could never get my system to boot into the smp kernel. So, I never took advantage of HT.

---

### Post by kpkeerthi on 2006-08-07
Yes... I did notice a (very minor) difference in idle cpu usage when running 686 kernel. And about the speed... I couldn't visibly see any difference and to the best of my knowledge, there isn't any benchmark that proves that 686 kernel runs faster than 386. Its very subjective. All that matters to me is stability.

---

### Post by skale on 2006-08-07
X doesn't work with the 686 kernel. Gosh darn, same speed. aptitude remove will get rid of it?

---

### Post by kpkeerthi on 2006-08-08
What video card do you have? nvidia? ATi? Did you remember to install linux-restricted-modules for the version of kernel you are running?

Boot with the 686 kernel and login in to a terminal session. Then do:
```

sudo aptitude install linux-restricted-modules-`uname -r`

```
(copy/paste the above command)

---

### Post by az on 2006-08-08
> **kpkeerthi said:**
> What video card do you have? nvidia? ATi? Did you remember to install linux-restricted-modules for the version of kernel you are running?


The linux-686 package takes care of that for you.

---

