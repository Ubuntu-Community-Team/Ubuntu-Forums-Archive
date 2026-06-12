---
title: "My super laptop is super slow on Hardy."
date: 2008-05-03
forum: General Help
---

### Post by fizgig on 2008-05-03
I've just installed Hardy on my new alienware which has a dual core 2.5GHz chip, an nvidia 8800m card and so forth.  I was expecting a pretty fast experience.  This is a WUBI install by the way....

Anyhow everything runs very slow.  I've installed the nvidia drivers and I get perfect resolution and compiz runs ok.  Glxgears gives me only ~950 which is much slower than my previous laptop.

In general, everything I do is preceeded by very noticable lag.

When I run top, firefox is taking 9% of the Cpu sometimes but that's the most any of them are taking.  There are a few processes running at 1% like xorg, metacity and so forth.  No obvious offenders.

I've even stopped the powernowd service but no difference.

Anyone have any tips with what I can do to get a responsive system?

---

### Post by fizgig on 2008-05-03
I installed the beta video driver from nvidia (1.71 or something like that) and things have greatly improved.

---

