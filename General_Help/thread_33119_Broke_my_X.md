---
title: "Broke my X"
date: 2005-05-09
forum: General Help
---

### Post by Eproxus on 2005-05-09
Trying to install the DRI drivers by following [this guide]("http://ubuntuforums.org/showthread.php?t=29990") I broke my X.org.

Now it says:
 ```
(WW) RADEON(0): Failed to set up write-combining range (0xe0000000,0x20000000)
```

I've tried using both "ati" and "radeon" as my device driver in xorg.conf but with the same results. 

Also, trying to repair the broken X I tried to install the DRI drivers from the debian repository provided but they halted half ways. Therefore when trying to reinstall xserver-xorg I get unresolved dependancies which cannot be repaired.

How can I restore my X?

---

### Post by Eproxus on 2005-05-09
Fixed it. Rebooted and used an old 2.6.8 kernel instead of 2.6.10 (which I was currently using). Then it booted correctly and gdm started. I reinstalled xserver-xorg and rebooted and used the 2.6.10 and it worked fine.

---

