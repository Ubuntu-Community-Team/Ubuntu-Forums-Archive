---
title: "Custom kernel - less RAM?!?"
date: 2008-07-06
forum: General Help
---

### Post by KOTAPAKA on 2008-07-06
I just compiled a new kernel. Everything is working fine but my system memory went down from 1024 to 885. I don't have any idea why. Any suggestions/experience?

---

### Post by PmDematagoda on 2008-07-06
Did you by any chance disable high memory support?

---

### Post by KOTAPAKA on 2008-07-06
Yes but I have less than 4 GB - just 1 GB of ram so it can be off, right?

---

### Post by PmDematagoda on 2008-07-06
> **KOTAPAKA said:**
> Yes but I have less than 4 GB - just 1 GB of ram so it can be off, right?

Not in my case(and it may be in yours), I have 1Gb of RAM and in my attempts to be as minimal as possible I also turned high memory support off and when I booted the kernel I only had 800+Mb of RAM, turning on high memory support fixed it, it should do the same in your case.

---

### Post by KOTAPAKA on 2008-07-06
> **PmDematagoda said:**
> Not in my case(and it may be in yours), I have 1Gb of RAM and in my attempts to be as minimal as possible I also turned high memory support off and when I booted the kernel I only had 800+Mb of RAM, turning on high memory support fixed it, it should do the same in your case.

10x mate. That did it. Really really thank you. I had compiled that kernel about 4 times now wondering why this issue arises.

---

