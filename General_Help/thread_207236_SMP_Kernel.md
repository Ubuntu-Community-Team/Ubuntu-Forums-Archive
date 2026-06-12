---
title: "SMP Kernel?"
date: 2006-07-01
forum: General Help
---

### Post by ions on 2006-07-01
$ uname -a
Linux tolstoy 2.6.15-25-k7 #1 SMP PREEMPT Wed Jun 14 11:43:20 UTC 2006 i686 GNU/Linux

I used Synaptic to install linux-k7.  I only have a AMD 3000+ running 32 bit Dapper.  Why did I end up with an SMP kernel?

---

### Post by Shigun on 2006-07-01
Because the k7 kernel supports SMP.

---

### Post by rbalfour on 2006-07-01
AMD 3000+ is SMP. It compared to the P4 3.06 HT CPU.

SMP is not only for dual CPU machines. But also dual-core and hyper-threading CPUs.

For ref: [http://www.linuxhardware.org/article.pl?sid=03/02/19/1544249&mode=thread](http://www.linuxhardware.org/article.pl?sid=03/02/19/1544249&mode=thread)

---

### Post by ions on 2006-07-01
There's no seperation between SMP and non SMP kernels?  Seems wasteful.

---

### Post by Shigun on 2006-07-01
[QUOTE=rbalfour]AMD 3000+ is SMP. It compared to the P4 3.06 HT CPU.

SMP is not only for dual CPU machines. But also dual-core and hyper-threading CPUs.

For ref: [http://www.linuxhardware.org/article.pl?sid=03/02/19/1544249&mode=thread](http://www.linuxhardware.org/article.pl?sid=03/02/19/1544249&mode=thread)[/QUOTE]

Negative.  The AMD Athlon 3000+ is neither dual-core, nor anything similar to hyper threading.  It is a single core processor.  As he does not have another processor in there, his system is not utilizing the SMP capabilities.

ion, I doubt there is any performance loss from having a kernel with SMP capabilities, versus one without.  If you wish to get a fully optimized kernel for your system exactly, you could compile your own kernel.  However, make sure you know what you are doing first.  I learned with installs of [Gentoo Linux](http://www.gentoo.org).

---

### Post by ions on 2006-07-01
Yeah I know how to compile my own kernel, also learned with Gentoo.  I'm just lazy.  One reason I came to Ubuntu.  Oh well, no real harm in having SMP I don't think.

---

