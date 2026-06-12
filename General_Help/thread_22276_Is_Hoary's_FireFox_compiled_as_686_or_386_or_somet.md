---
title: "Is Hoary's FireFox compiled as 686 or 386 or something else?"
date: 2005-03-26
forum: General Help
---

### Post by wernst on 2005-03-26
All,

Out of curiosity, is the FireFox package that I get from the Hoary repositories compiled at a 686 package, or something else?

I ask because the Mozilla site is offering me the 686-package to download and install, but I wouldn't bother if I already have a 686-optimized version...

-Warr

---

### Post by jdong on 2005-03-26
All Ubuntu packages are compiled for the 486 instruction set with Pentium4 optimizations (-march=i486, -mcpu=pentium4).

I doubt you'll see any better performance with the official version, and the official version also doesn't do Debian integration very well...

---

