---
title: "Urgent help with xorg"
date: 2007-11-06
forum: General Help
---

### Post by khalid1100 on 2007-11-06
I tried to connect the laptop to projector and tried to active the second display through the dispaly manager. It asked me to restart but then xorg failed to restart the GDM.
Please help urgently I have important presentation.

---

### Post by knutschr on 2007-11-06
You probably have an automatic made backup.
In recovery mode, type
sudo mv /etc/X11/xorg.conf~ /etc/X11/xorg.conf

---

