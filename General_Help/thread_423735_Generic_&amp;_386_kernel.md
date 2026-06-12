---
title: "Generic &amp; 386 kernel"
date: 2007-04-26
forum: General Help
---

### Post by Beliar on 2007-04-26
Hello,
I was lately wondering about the difference between the generic kernel and the 386 kernel. I mean you cant run a powerpc kernel on x86 hardware anyway, so whats so generic about that kernel??
And the 686 kernel package says for upgrade only, whats that about?

Does the 386 kernel have less hardware detection or is it optimized for 386 kernel? 

Another thing I've been asking myself, is why the meta package linux or linux-386 are not used. These depend on the latest kernel image and the latest restricted modules. These are installed independent atm. 

TIA,
greets, Beliar

---

### Post by kagashe on 2007-04-26
> I was lately wondering about the difference between the generic kernel and the 386 kernel. I mean you cant run a powerpc kernel on x86 hardware anyway, so whats so generic about that kernel??
And the 686 kernel package says for upgrade only, whats that about?

Till Dapper you had to install 686 Kernel after installation (installation installed 386 Kernel).

Since Edgy, the installation installed generic Kernel and you don't have to install 686 Kernel at all.

686 Kernel is now available only for upgrading Dapper (and previous releases) from 386 to 686.

Hope this answers your question.

kagashe

---

### Post by Beliar on 2007-04-26
Thank you very much!
At least it answered the question concerning linux 686, but whats now the difference between generic kernel and 386 kernel?

---

### Post by Tomosaur on 2007-04-26
The generic (686) kernel has support for SMP (Symmetric Multi-Processing), which is what a lot of modern computers are capable of. The 386 kernel does not have this feature.

---

### Post by Beliar on 2007-04-26
Ah ok thanks, 
So my pentium-m (dothan i think) has no hyper-threading, just one core and only one cpu, so I could also use the 386 kernel. Which is maybe a bit smaller becaue thats not compiled in?
Hmm, however, another mystery solved, :)

THX,
Beliar

---

### Post by az on 2007-04-26
The 386 kernel is now the generic kernel.  The features of the 686 kernel have become runtime options, and not compiletime options, which means the extra instructions and features are autodetected and enabled when you boot the generic kernel.

Of course, the generic kernel (386) does do SMP.

---

