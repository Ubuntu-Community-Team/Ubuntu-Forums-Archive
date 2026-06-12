---
title: "skge and ipx =&gt; kernel panic."
date: 2005-10-21
forum: General Help
---

### Post by jotape99 on 2005-10-21
Hello,

I've a marvell yukon nic (gigabit) with skge driver. When I install the ipx package, I've a kernel panic. It's seems to be an incompatibility between this driver and the ipx package needed to access a novell server. Ipx works when the nic is disabled and using another card (3com 2C905)

Versions:
kernel: 2.6.19-9-686
ipx: 2.2.6-1

Any suggestions ?

EDIT: I've tried to load the sk98lin diriver instead of the skge but with no great result.

---

