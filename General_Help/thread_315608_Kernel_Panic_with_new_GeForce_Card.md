---
title: "Kernel Panic with new GeForce Card"
date: 2006-12-09
forum: General Help
---

### Post by Clodaus on 2006-12-09
I've just installed a new GeForce FX 5500 OC graphics card on my already working Ubuntu system. However, when I booted it after the installation, Ubuntu stopped loading, complaining about a kernel panic.

So I tried to reinstall ubuntu. I tried booting the live CD for Edgy, and the same problem, just a different error about a null pointer. I know the graphics card works - it works perfectly in my Windows installation. Does anyone have any ideas?

---

### Post by Clodaus on 2006-12-09
Okay I've disabled the PCI slots and got into Linux - is there any driver I can blacklist to prevent this problem?

Thanks

---

### Post by Clodaus on 2006-12-09
Okay nevermind guys I fixed it :) I added the following lines to blacklist:

blacklist intel_agp
blacklist agpgart

---

