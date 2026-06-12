---
title: "Nvidia Driver"
date: 2008-03-31
forum: General Help
---

### Post by reyhan on 2008-03-31
okey here it is i just install Digital allience Graphic card it has NVIDIA GPU 7300GS PCIEx16 on my motherboard, after that why i can't boot to ubuntu it just blank screen whats happening?

---

### Post by kpkeerthi on 2008-03-31
From GRUB, boot into recovery mode.

At the command prompt, type
```
dpkg-reconfigure -phigh xserver-xorg
```

Choose 'vesa' for driver and the supported resolutions. Reboot normally.

When you get to the Desktop, install nvidia binary driver, using [restricted drivers manager]("https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia")

---

### Post by reyhan on 2008-03-31
okey i will try it

---

### Post by reyhan on 2008-03-31
i just run ```
dpkg-reconfigure -phigh xserver-xorg
``` and finish install the driver in Restricated Drivers manager and why i can't change the screen resolution?

---

### Post by PmDematagoda on 2008-03-31
What do you mean that you cannot change the screen resolution, could you please be more specific.

---

