---
title: "Open drivers"
date: 2007-03-06
forum: General Help
---

### Post by djaam on 2007-03-06
I have radeon 9200 with fglrx drivers 

I use ubuntu 6.06 and i want use AIGLX to run Compiz/Beryl, but for AIGLX open drivers is needed, right? On open drivers direct rendering is working.... but how to install this drivers?

---

### Post by djaam on 2007-03-07
.

---

### Post by djaam on 2007-03-07
Anyone?

Btw. Ubuntu 6.10 have Open drivers that use 3d?

---

### Post by kaamos on 2007-03-07
The driver is already installed. Change
```

Driver      "fglrx"

```
to
```

Driver      "radeon"

```
in /etc/X11/xorg.conf and reboot (or just rmmod/modprobe the modules, booting is simpler). Then just use glxgears -printfps to verify you have working 3d.

---

### Post by djaam on 2007-03-07
> **kaamos said:**
> The driver is already installed. Change
```

Driver      "fglrx"

```
to
```

Driver      "radeon"

```
in /etc/X11/xorg.conf and reboot (or just rmmod/modprobe the modules, booting is simpler). Then just use glxgears -printfps to verify you have working 3d.

Thanks... but when GDM is needed to load, i get BLACK SCREEN (no informations, just black screen, GDM isnt loading) ....

---

