---
title: "apt-get -b source"
date: 2007-04-05
forum: General Help
---

### Post by Megatog615 on 2007-04-05
Is there a way to make "apt-get -b source" to use -O3 for optimization, among other things like -march, instead of just -O2? I'd like to build a couple things from source for optimization reasons.

---

### Post by ben.s on 2007-04-05
Unless you wrote the software in question or have something from the developer saying that -O3 will give you better performance than -O2, I wouldn't bother.  -O3 optimizations can actually make the code perform *worse* than -O2 in a lot of situations, on many different processors.

---

