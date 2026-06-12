---
title: "Kernel for 686 in Edgy."
date: 2006-10-31
forum: General Help
---

### Post by kagashe on 2006-10-31
Hi,

Till last Ubuntu distribution I was installing Linux-image-686 after the default installation.

I understand in Edgy the generic Linux image is installed and Linux-image-686 is not required.

Is this correct?

kagashe

---

### Post by engineer on 2006-10-31
i don't know why, but edgy was installing new i386 versions all the time.
i mean since i changed to edgy beta, i only got i386 versions

---

### Post by displague on 2006-10-31
The linux-image-686 package has been replaced with linux-image-generic.  The same is true for linux-image-k7.  The "generic" line now carries support for modern desktop systems (i686/k7), including SMP support.

The linux-image-server line caters to server systems and processors.

---

### Post by kagashe on 2006-10-31
> **displague said:**
> The linux-image-686 package has been replaced with linux-image-generic.  The same is true for linux-image-k7.  The "generic" line now carries support for modern desktop systems (i686/k7), including SMP support.

The linux-image-server line caters to server systems and processors.
Thanks.

kagashe

---

### Post by clickwir on 2006-11-01
> **displague said:**
> The linux-image-686 package has been replaced with linux-image-generic.  The same is true for linux-image-k7.  The "generic" line now carries support for modern desktop systems (i686/k7), including SMP support.

The linux-image-server line caters to server systems and processors.

Such as.....?

I ask because I have a Compaq Proliant 1850R "server" that uses PIII500mhz cpus. Not much different than a "desktop" cpu really.

---

### Post by eppoh on 2006-11-03
I had upgraded to i686 in Badger and this one seems slower.
Is there a 686 optimized kernel available?

---

### Post by dpm on 2006-11-03
> **eppoh said:**
> I had upgraded to i686 in Badger and this one seems slower.
Is there a 686 optimized kernel available?

"seems slower" is not really a measure. Benchmarks are.

Please read the story behind this on this thread from the ubuntu development list:

[https://lists.ubuntu.com/archives/ubuntu-devel/2006-August/019983.html](https://lists.ubuntu.com/archives/ubuntu-devel/2006-August/019983.html)

In short, it was proved that the difference in performance between the different kernels was insignificant and the gain in maintenance ease (1 kernel package instead of several ones) outweighed the gain in performance.

In any case, the 686 and 386 kernels are still available from the repos.

Cheers.

---

### Post by eppoh on 2006-11-04
tried to get install the i686 kernel and no package was found,
Where is it available.

---

