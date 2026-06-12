---
title: "kernel panic fatal exception in interrupt"
date: 2007-11-19
forum: General Help
---

### Post by cnschulz on 2007-11-19
Hi, I have been running fiesty and then gutsy for some time with no problems. No I am recieving a kernel panic. "kernel panic fatal exception in interrupt" i believe this is due to disk activity. I noticed it was happening whenMunin was running so i disabled it. The machine then ran fine (only tested 30 mins) then id did an fsck and recieved the panic again. It looks bad!

ive seen some posts regarding doing a reinstall of the kernel. should i attempt that? is there something else i can try? 

cheers

c.

---

### Post by cnschulz on 2007-11-22
Hi, 

 it turned out to be dud memory. Removed offending chip and all is well (albeit slower!)

Thanks.

c.

---

