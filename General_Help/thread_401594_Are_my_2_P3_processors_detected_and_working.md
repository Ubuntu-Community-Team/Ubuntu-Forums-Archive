---
title: "Are my 2 P3 processors detected and working?"
date: 2007-04-04
forum: General Help
---

### Post by Mrlush123 on 2007-04-04
I am having some trouble. I have an old computer that has an ASUS P2B-D motherboard that supports two Pentium 3 processor on it. I have 2 processors on it. Does ubuntu 6.06 work with them?

I have it all installed on the computer but I dont think it works right. It seems that both processors are not detected. When I go to sys info it only shows one processor. When I go to system monitor i only see one processor. Even my device manager sees only one processor. Is there something I can do to set it up correctly. 

When I am booting up 2 processor are detected. It just seems that it is not detected in Ubuntu. How can I be sure? Or how can i configure it?

:confused:<br /><br />
----------------------------------------<br />

----------------------------------------<br />

---

### Post by crispy_420 on 2007-04-05
Little old but this may get you going in the right direction:

[http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/594004372731/inc/-1](http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/594004372731/inc/-1)

Look into your kernel.

---

### Post by mcduck on 2007-04-05
Just install the linux-686-smp package to get the right kernel with support for multi-CPU/multi-core machines :)

---

### Post by Mrlush123 on 2007-04-06
I installed the 686 and it works fine. Its just that I have the Nvidia card on there. Do you know how do set that up with it?

---

