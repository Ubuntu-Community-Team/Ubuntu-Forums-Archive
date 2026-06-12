---
title: "RAM frequency / latency utility for Linux?"
date: 2007-06-12
forum: General Help
---

### Post by moron on 2007-06-12
Howdy.  I am curious if there is a tool that exists for Linux which will show the current RAM timings?  The reason I need this is that the motherboard I have (Asus M2a-VM) does not support manual adjustment of latency settings and I want to know what it is currently running with so as to see if they are reasonable for the RAM I have installed.  

If you know of such a tool please let me know (command line or otherwise).

Cheers

---

### Post by revertex on 2007-06-13
nor lm-sensors, lshw or hwinfo can, try central brain identifier, is a windoze app, but run under wine.

[http://cbid.amdclub.ru/](http://cbid.amdclub.ru/)

(no, i'm not affiliated with this site in any way)

---

### Post by moron on 2007-06-13
Thanks for the response.  Looks like lshw does not do what I want exactly though it offers a nice summary none the less. . .

I am looking for something to compare against RAM latency specs like "CL 4-4-4-12".   I'll see if any of the other non Windows options will do that when I get home.

Cheers!

---

### Post by CrispyFried on 2007-06-13
if memtest86 is in your boot menu, run that. it should tell you. but Im not sure if it just reads it out of the spd chip or actually reports the current value.

---

### Post by revertex on 2007-06-14
> **CrispyFried said:**
> if memtest86 is in your boot menu, run that. it should tell you. but Im not sure if it just reads it out of the spd chip or actually reports the current value.

i misunderstood the question, and  discarted memtest because it runs before linux.

Yes, CrispyFrield is right, memtest can read the actual timmings.


[[IMG]http://www.memtest.org/pics/nf2-big.gif[/IMG]]("http://www.memtest.org/pics/nf2-big.gif")

---

