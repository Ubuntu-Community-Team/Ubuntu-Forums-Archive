---
title: "64 bit ubuntu -&gt; 64 bit packages?"
date: 2013-02-15
forum: General Help
---

### Post by zomgwhat on 2013-02-15
Hi, forgive me if this is a totally noob question, but I have a 64 bit install of ubuntu - does that mean all of the packages available through synaptic will be the 64 bit versions of the software? In particular I've installed the LAPACK and BLAS linear algebra packages - I've been told the 64 bit versions of these are considerably faster than the 32 bit versions, but it doesn't say in synaptic if they're 64 or 32 bit. Is there a way to check, or will they definitely be 64 bit? Thanks!

---

### Post by fantab on 2013-02-15
Yes, all the packages will be 64bit... except for certain applications, like Skype, which is not available for Linux 64bit we need 32bit libraries which are automatically handled by Synaptic, you don't have to worry too much... If your packages are available for linux in 64bit then Synaptic will install 64 bit only.

---

### Post by oldos2er on 2013-02-15
32-bit packages will be marked with :i386; the rest you can assume are 64-bit.

---

### Post by Bufeu on 2013-02-15
32-bit packages will be marked with :i386; all others are 64-bit packages.

---

### Post by zomgwhat on 2013-02-15
great, thanks guys!

---

