---
title: "Wake on lan not working on 13.04 (works fine on 12.04)"
date: 2013-05-05
forum: General Help
---

### Post by Soul77 on 2013-05-05
Any idea why Wake on lan not working on ubuntu 13.04? It is working fine on 12.04.
I'm running it on my new HP Proliant Microserver N40L

---

### Post by markbl on 2013-05-06
> **Soul77 said:**
> I'm running it on my new HP Proliant Microserver N40L
If you have changed to a new PC then it has nothing to do with 12.04 cf 13.04. You need to enable PCI/PCIe WOL in your bios.

---

### Post by Squalo71 on 2014-02-27
How did you enable WOL on 12.04? Have you used the **ethtool** command? If yes, remember to put the command in **/etc/rc.local**.

---

