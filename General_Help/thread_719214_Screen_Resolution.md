---
title: "Screen Resolution"
date: 2008-03-08
forum: General Help
---

### Post by nigel_salvador on 2008-03-08
I've changed my screen resolution, however when I login into my computer the monitor indicates that the video signal is out of range and there is no image on the screen. Please help

---

### Post by taurus on 2008-03-08
Boot into recovery mode from GRUB menu and reconfigure your X server again.

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

---

