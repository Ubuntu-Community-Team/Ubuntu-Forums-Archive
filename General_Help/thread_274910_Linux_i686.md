---
title: "Linux i686"
date: 2006-10-10
forum: General Help
---

### Post by ricanelite on 2006-10-10
What is Linux i686 is that a special Computer? Or a Special Linux Operating System?

---

### Post by az on 2006-10-10
i386 is the CPU architecture.  i686 has common instructions with i386 and so anything that is built (a program that is compiled) for i386 will run on 686.  AMD CPUs have even more instructions.  They use the K7 (or k8 for 64-bit) architecture.  Again, anything compiled for 386 will run on a K7 processor.

The next version of Ubuntu will ship with only the i386 kernel, with the ability to enable more instructions at boot time.  

That's why previous versions of Ubuntu have linux-386, linux-686, linux-k7 kernels available.

They are just the kernel which are compiled with certain optimisations for those arches.

---

### Post by jdunn on 2006-10-10
Linux-x86 = kernels for Intel family of processors
      |
      |--- Linux-386 = kernel for 386 processor or newer
      |--- Linux-686 = kernel for Pentium processors
      |--- Linux-686smp = kernel with symmetric multiprocessing (multi-core and hyperthreading) for Pentium processors

Linux-k7 =  kernel for AMD processor
Linux-ppc = PowerPC kernel (for apple computers)

Linux-386 is the lowest common denominator (will run on everything, except ppc)
If you have a Pentium processor, most people would tell you to use Linux-686 or 686smp.

---

### Post by ricanelite on 2006-10-10
Got you, the reason why I'm asking is cause my Jobs company will be releasing a Version of our software for Linux i686, Bascially it is a Java Application that needs Java 5 to run on Windows. So I was wondering if it is possible to use that Application that is used on our windows machine and try to run it on Ubuntu Linux.

Because the file you download to install the Application file name is  ***main.jnlp***

So will be it possible for my to run that File on Linux?

---

### Post by TigerWolf on 2006-10-10
Since its using Java it should be fine to run it on linux.

---

### Post by PriceChild on 2006-10-10
> **azz said:**
> The next version of Ubuntu will ship with only the i386 kernel, with the ability to enable more instructions at boot time.Actually it will be called "linux-generic". There is a few threads in the edgy dev forum explaining the change if you would like to take a look.

---

### Post by ricanelite on 2006-10-11
How would I be able to run that application **main.jnlp**? Do I need to use wine? Or is there a different method of getting it installed.

Also where can I go and download Wine, and also How do I install it. 

Now please make it simple as possible because I'm a Linux Newbie!!!

Thanks everyone for the response.

---

