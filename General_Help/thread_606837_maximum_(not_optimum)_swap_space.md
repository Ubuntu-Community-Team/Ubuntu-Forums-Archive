---
title: "maximum (not optimum) swap space"
date: 2007-11-08
forum: General Help
---

### Post by etola on 2007-11-08
is there a technical limit on the maximum amount of swap space ? 

please don't tell me optimum size is this and that because I need a huge swap (~10G) for some experiments I'm running and I really need it.

so my question is about the maximum limit not optimum one ...

( I got a 64-bit Intel WS  with dual xeon cpu and 4GB RAM  )

---

### Post by atlfalcons866 on 2007-11-08
4.4.2. How large can my swap space be?

Currently, the maximum size of a swap partition is architecture-dependent. For i386, m68k, ARM and PowerPC, it is "officially" 2Gb. It is 128Gb on alpha, 1Gb on sparc, and 3Tb on sparc64. An opteron on the 2.6 kernel can write to a 16 Tb swap partition. For linux kernels 2.1 and earlier, the limit is 128Mb. The partition may be larger than 128 MB, but excess space is never used. If you want more than 128 MB of swap for a 2.1 and earlier kernel, you have to create multiple swap partitions (8 max). After 2.4, 32 swap areas are "officially" possible. See setting up swap for details.

footnote: "official" max swap size: With kernel 2.4, the limit is 64 swap spaces at a maximum of 64Gb each, although this is not reflected in the man page for mkswap. With the 64 bit opteron on the 2.6 kernel, 128 swap areas are permitted, each a whopping 16 Tb! (thanks to Peter Chubb for the calculation)

---

