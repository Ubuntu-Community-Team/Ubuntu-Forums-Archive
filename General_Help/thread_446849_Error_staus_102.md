---
title: "Error staus 102"
date: 2007-05-17
forum: General Help
---

### Post by Brian Carruthers on 2007-05-17
I have a broken package (Samba) which I can't remove. This prevents my software updates...

I attempted to fix the problem in package manager with the following error:
E: /var/cache/apt/archives/samba_3.0.22-1ubuntu3.3_i386.deb: subprocess new pre-removal script returned error exit status 102

Any help would be appreciated.

Thanks

---

### Post by jmendez2 on 2007-05-26
try doing this.
from a terminal window type:  sudo rm /etc/rc2.d/K09samba

then via synaptic re-install samba

hope that works.

---

