---
title: "Fiesty Fawn: Linux Kernal - generic Vs 386"
date: 2007-06-22
forum: General Help
---

### Post by eabhi on 2007-06-22
Whats the difference between the Linux Kernel Image -generic and -386??? which one is the best for AMD Athlon XP Processors???

I have Desktop and laptop both having 32-bit AMD Athlon XP Processors. I have Clean installed Feisty Fawn on the Desktop and upgraded from Ubuntu 6.06->6.10->7.04 on the laptop.

Now the case is that the Desktop uses the "-generic" Kernel image while the Laptop uses the "-386" kernel. If both have the same Processor, why is the installations using the different type/flavour of the Kernel :(

Please let me know which oe is the best of both and how to switch to the one from the other kernel. :)

Cheers
eabhi

---

### Post by stchman on 2007-06-22
> **eabhi said:**
> Whats the difference between the Linux Kernel Image -generic and -386??? which one is the best for AMD Athlon XP Processors???

I have Desktop and laptop both having 32-bit AMD Athlon XP Processors. I have Clean installed Feisty Fawn on the Desktop and upgraded from Ubuntu 6.06->6.10->7.04 on the laptop.

Now the case is that the Desktop uses the "-generic" Kernel image while the Laptop uses the "-386" kernel. If both have the same Processor, why is the installations using the different type/flavour of the Kernel :(

Please let me know which oe is the best of both and how to switch to the one from the other kernel. :)

Cheers
eabhi

The -386 kernels typically do not support SMP.

---

### Post by kpkeerthi on 2007-06-22
linux-image-generic was introduced in Feisty. This package selects the kernel image that best suits your processor architecture. In my case, it installed i686 version of the kernel for my Pentium Mobile. 

On your laptop, you may still install linux-image-generic using synaptic and remove the -386 kernel. You are still running the -386 kernel as you upgraded from Dapper where the generic kernel never existed. 

Also, I suggest you to install the -generic kernel as it automatically takes care of the dependency on the releted kernel modules required for your system. For instance, it automatically installs the corresponding linux-restricted-modules if required.

---

### Post by eabhi on 2007-06-23
Thanx a lot kpkeerthi... I would change the kernel from -386 to -generic using synaptic package manager... 

but can I remove the -386 and install generic at the same go??? I think it didn't allow me to remove the -386 kernel :( Do I need to install -generic kernel... boot using it and then remove the -386???

Also how/where do u know that it installed i686 version of kernal??? :confused:

> **kpkeerthi said:**
> linux-image-generic was introduced in Feisty. This package selects the kernel image that best suits your processor architecture. In my case, it installed i686 version of the kernel for my Pentium Mobile. 

On your laptop, you may still install linux-image-generic using synaptic and remove the -386 kernel. You are still running the -386 kernel as you upgraded from Dapper where the generic kernel never existed. 

Also, I suggest you to install the -generic kernel as it automatically takes care of the dependency on the releted kernel modules required for your system. For instance, it automatically installs the corresponding linux-restricted-modules if required.

---

