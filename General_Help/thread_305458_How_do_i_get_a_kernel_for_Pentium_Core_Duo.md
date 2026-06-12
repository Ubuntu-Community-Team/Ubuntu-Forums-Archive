---
title: "How do i get a kernel for Pentium Core Duo"
date: 2006-11-23
forum: General Help
---

### Post by Athanasius on 2006-11-23
I installed edgy on my new Dell with a Pentium Core Duo processor and things seem to be working fine but I think I might need a customized kernel because I think my computer is supposed to be working better than it already is.

how do I go about getting a proper kernel for my system?

---

### Post by NetworkGuy on 2006-11-23
From a terminal type ```
uname -a
```

If you see something like > Linux R40-laptop 2.6.17-10-generic #2 **_SMP_** Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux then you are running a kernel that sees your duo processor (Note the SMP)

Also from a terminal, typing ```
top
``` will give you stats on howyour system is running.  You should stats for two processors near  the  top of the screen.

---

### Post by Athanasius on 2006-11-23
should i be using the generic kernel that edgy uses?  I was trying to get Beryl to work and it said that I had to use a certain kernel so I changed to  2.6.17-10-386.  That one says nothing about SMP.  What does it mean anyways?

---

### Post by phillips321 on 2006-11-23
basically you need to upgrade your kernel to one that supports a pc with more than one cpu core, SMP stands for Symmetric Multiprocessing (more than one core).

Sadly i'm not sure how to add a customer kernel to ubuntu exactly, maybe someone else here has an idea, coz i've never been blessed with a dual core cput yet....xmas is near :)

p.s. a search for SMP in Synaptic Package Manager shows *linux-k7-smp*. This is detailed as support for AMD Duron/Athlon processors with SMP support, maybe it will support your intel cpu aswell?

---

### Post by clownius on 2006-11-24
Personally ive changed my kernel a few times and generally update it via Synaptic package manager.  The only rule ive learned the hard way is dont try and uninstall your current kernel untill u reboot its a quick way to amke everything grind to a halt.
I have a Core 2 Duo arriving Thursday next week so will be trying to get eveything up and going then. I will be trying "linux-686-smp" based on the fact its an intel multi-processor sytem but others may have better ideas im still relativly new to linux but im never afraid to have a hack at something.
Moving my current Celeron to the standard 686 kernel from the 386 just seemed to make everything run faster and smoother.

Clownius

---

### Post by NyquistLimit on 2006-11-24
The generic kernel is the one you should be using because it incorporates support for all CPUs, including SMP. The change was made in edgy to avoid having to use different kernel packages.

---

### Post by bettola on 2006-11-24
where in edgy we can change to use 2 cpus? i have the same problem...latest generic kernel but no dual processor

---

### Post by stbaker on 2006-11-24
The generic edgy kernel already does support dual cpu's, out of the box. I'm currently running it on my lenovo T60 with core duo, and it works just fine.

---

### Post by clownius on 2006-11-25
I will believe the others as im still using dapper here and in the middle of upgrading to edgy.  Personally id still try the change if it wasnt reporting the 2 cpus at worst u get practice reinstalling lol

---

### Post by UberGeekInc on 2006-12-09
> **Athanasius said:**
> I installed edgy on my new Dell with a Pentium Core Duo processor and things seem to be working fine but I think I might need a customized kernel because I think my computer is supposed to be working better than it already is.


To confirm your kernel is aware of both CPUs do `cat /proc/cpuinfo`.

> how do I go about getting a proper kernel for my system?

*kernel-package*

You can get help here: 

[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

---

