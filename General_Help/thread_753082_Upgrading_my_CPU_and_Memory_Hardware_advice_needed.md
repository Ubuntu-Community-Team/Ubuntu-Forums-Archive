---
title: "Upgrading my CPU and Memory Hardware advice needed"
date: 2008-04-12
forum: General Help
---

### Post by Robbyx on 2008-04-12
Can Ubuntu handle the dual cores? I am about to buy the intel e8200 and am wondering if I should aim to fill all memory slots or keep to just two slots one core?

Robin

---

### Post by wdaniels on 2008-04-12
Yes, SMP support is available by default in newer kernels, including the generic ubuntu kernel.  How well multiple cores are utilised though also depends on the specific applications being used.  As far as memory goes, you don't have dedicated slots for each core - it doesn't matter how many slots you use.  As a guide for total RAM, I can only say that I have 2Gb in my main linux desktop and have never yet felt that I would gain more than a nominal performance benefit (basically from extra disk caching) by adding more, but if you play a lot of heavy games, maybe you could use more.

---

### Post by Robbyx on 2008-04-12
Following your comments, for which I thank you, I will not buy the memory but will upgrade the CPU. I watch films on the computer so I thought I would gain from the extra memory, however I will hold back until I see how the new cpu works. In the meantime I have a query about my current memory. It is corsair. Ubuntu is recognising that I have 2g installed. When  I start the machine the memory test ends at about 250 megs (I am wrong on the actual number but is is far short of the full memory load). Is this anything to worry about?

Robin

---

### Post by wdaniels on 2008-04-13
I think that is most likely the memory of the graphics card, and the number would likely be 256Mb.  In any case, if Ubuntu sees 2Gb then there's nothing to worry about.

---

