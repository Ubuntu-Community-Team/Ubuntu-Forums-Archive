---
title: "OHCI Host Controller - boot stops"
date: 2006-08-16
forum: General Help
---

### Post by djsamsel on 2006-08-16
i just upgraded from a nvidia 7600 to a 7800 (same manufacturer). now i lock at OHCI line everytime. any suggestions?

---

### Post by zxee on 2006-08-16
Did you have the propritary nvidia driver installed?
You could either boot into safe mode or use the live cd and edit your /etc/X11/xorg.conf file replacing "nvidia" with "nv" and if that works you can re-install the nvidia driver for your new card.

---

