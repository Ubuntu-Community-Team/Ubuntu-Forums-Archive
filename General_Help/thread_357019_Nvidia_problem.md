---
title: "Nvidia problem"
date: 2007-02-09
forum: General Help
---

### Post by krissis on 2007-02-09
I have a Nvidia GeForce 6800 graphic card and i used this guide for installing the driver for it: [http://albertomilone.com/latest_nvidia_udsf_edgy.html](http://albertomilone.com/latest_nvidia_udsf_edgy.html). I couldn't install nvida-glx, i could only install legacy drivers, is that bad? Is legacy drivers worser than normal drivers, and is there a way fix it, if it need to be fixed? :KS

---

### Post by daou on 2007-02-09
The method there looks a bit old.

Look at the Beryl method for installing nVidia drivers:

[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA")

Only do the section marked: "Installing the nVidia driver"
2.1 First method
2.2 Driver installation

then stop before 2.3 (second method).

---

### Post by daou on 2007-02-09
Only these nvidia cards need the legacy driver:

> RIVA TNT 0x0020
RIVA TNT2/TNT2 Pro 0x0028
RIVA TNT2 Ultra 0x0029
Vanta/Vanta LT 0x002C
RIVA TNT2 Model 64/Model 64 Pro 0x002D
Aladdin TNT2 0x00A0
GeForce 256 0x0100
GeForce DDR 0x0101
Quadro 0x0103
GeForce2 GTS/GeForce2 Pro 0x0150
GeForce2 Ti 0x0151
GeForce2 Ultra 0x0152
Quadro2 Pro 0x0153

---

### Post by krissis on 2007-02-09
Thanks! it worked :)

:guitar:

---

