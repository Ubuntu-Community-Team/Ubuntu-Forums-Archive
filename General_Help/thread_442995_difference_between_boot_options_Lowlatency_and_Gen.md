---
title: "difference between boot options Lowlatency and Generic?"
date: 2007-05-14
forum: General Help
---

### Post by chunchengch on 2007-05-14
I have many options to boot Ubuntustudio, but I don't understand what is the difference between options "Ubuntu, kernel 2.6.20-15-lowlatency" and "Ubuntu, kernel 2.6.20-15-generic"?

---

### Post by mcduck on 2007-05-14
Generic kernel is normal Linux kernel, suitable for everyday use. It balances well between many applications running.

Low-latency kernel is for audio production in Ubuntu Studio, giving 95% of CPU time to current running program, to guarantee perfect recording and audio quality, and to keep the latency of your audio software in minimum.

Use the low-latency kernel when working with audio, but for everything else you should choose the generic one instead.

---

### Post by chunchengch on 2007-05-14
mcduck,

It is much helpful for me to select the most suitable boot option, thanks a lot!:)

---

### Post by mjitkop on 2007-05-15
Thanks mcduck for this explanation. What about video editing? Any problems of latency too with synchronization video/audio?

---

