---
title: "uninstalling broken packages"
date: 2008-04-18
forum: General Help
---

### Post by rocker9455 on 2008-04-18
i have a very stubborn package on my system (moblock-nfq) it wont uninstall when i use sudo aptitude remove moblock-nfq -f it says its locked by a sub-process (/usr/bin/dpkg) so i cant uninstall it at all and i am unable to install / uninstall anything

please help

---

### Post by kpkeerthi on 2008-04-18
Reboot and try again. Make sure only one of these synaptic/dpkg/aptitude/apt-get are running at a given time.

---

### Post by Tomatz on 2008-04-18
Boot into recovery mode then:

**sudo apt-get remove moblock-nfq**

---

### Post by AlphaWu on 2008-04-18
> **Tomatz said:**
> Boot into recovery mode then:

**sudo apt-get remove moblock-nfq**

Then run: sudo apt-get autoremove

---

### Post by rocker9455 on 2008-04-18
none of these works i tried rebooting into recovery mode and then sudo apt-get remove moblock-nfq but it says it is still blocked by dpkg

---

### Post by Tomatz on 2008-04-18
Go into synaptic and use the "fix broken packages" option.

---

### Post by rocker9455 on 2008-04-18
that didn't work either i just reinstalled ubuntu instead it was quicker than trying to uninstall it thanks all the same though :D

---

