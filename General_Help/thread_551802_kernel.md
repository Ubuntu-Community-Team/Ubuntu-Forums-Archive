---
title: "kernel?"
date: 2007-09-15
forum: General Help
---

### Post by Chymera on 2007-09-15
could anyone tell me what exactly the kernel is and where it is stored?

---

### Post by pheeror on 2007-09-15
Nice question :-) It's big piece of code, that cares about things like cpu scheduling, hardware resources, memory managment, filesystems and so on. Sources of linux kernel can be obtained on kernel.org. Ubuntu stores compiled ready to boot kernel in /boot

---

### Post by Chymera on 2007-09-15
sao is it just one big file? i heard somewhere smth about linux kernels being modular (which in my conception means "puzzled together out of interchangable pieces")

---

### Post by tht00 on 2007-09-15
> **Chymera said:**
> could anyone tell me what exactly the kernel is and where it is stored?

As pheeror said, it is compiled and installed to your /boot folder.

It basically handles all low-level operations and interaction to the physical hardware.

> **Chymera said:**
> sao is it just one big file? i heard somewhere smth about linux kernels being modular (which in my conception means "puzzled together out of interchangable pieces")

The Linux kernel is Monolithic by design... though, the full implications of that, I don't understand.

But I've compiled many kernels while working with Gentoo.  Really, when you configure the kernel, you can alter it's behavior, hardware options, and what drivers are compiled.  Now, options tend to be either compiled in or not.  Some options (mostly hardware drivers) can be left out, compiled into the kernel, or compiled as a module.  Modules can be loaded and unloaded later.  If it's compiled in, it can't be removed without the kernel reconfigured, recompiled, and a reboot.

---

### Post by Chymera on 2007-09-16
my boot folder has only 33 mb is the kernel really THAT small? and where exactly is it.... i've looked for it but wasnt able to find it.... then again i'm not really that sure what i'm supposed to look for....

---

### Post by pheeror on 2007-09-23
There are probably lots of kernels in your /boot ;-)
Kernel in my router has approx 1MB. 
What do you suppose to find, when you find that kernel? :-)

---

### Post by por100pre1 on 2007-09-23
> **tht00 said:**
> 
The Linux kernel is Monolithic by design... though, the full implications of that, I don't understand.


Wikipedia has the [answer]("http://en.wikipedia.org/wiki/Monolithic_kernel") to that.

---

### Post by oldos2er on 2007-09-23
Usually it's /boot/vmlinuz

---

