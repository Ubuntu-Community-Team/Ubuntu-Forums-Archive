---
title: "CPU Speed lower than normal?"
date: 2008-02-25
forum: General Help
---

### Post by b0ng0 on 2008-02-25
I recently overclocked my CPU from 2.2 GHz to 2.5 GHz (as well as my RAM). However, when I look in Ubuntu, it seems to say my CPU is 2.2 GHz. Is there anyway to check the actual FSB of my CPU in Ubuntu? (e.g. a Linux equivalent to CPU-Z).

---

### Post by Existentialist on 2008-02-25
Run:

cat /proc/cpuinfo

This will have a section telling you what speed it is running at (not fsb, but should tell you what you need to know).  The 2.2GHz may just be part of the processor name, and not actually the speed it is running at.

---

