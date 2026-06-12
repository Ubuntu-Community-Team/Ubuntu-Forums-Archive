---
title: "Feisty Kernel 2.6.20-14-386 with nvidia driver"
date: 2007-04-05
forum: General Help
---

### Post by raptor2552 on 2007-04-05
After this afternoons update of 7.04 my computer would not boot complaining about /etc/X11/xorg.conf being incorrectly configured.

After changing:
Section "Device"
        Identifier      "nVidia Corporation NV43 [GeForce 6600 GT]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection

to:
Section "Device"
        Identifier      "nVidia Corporation NV43 [GeForce 6600 GT]"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection

Kernel 2.6.20-14-386 booted without incident

Kernel 2.6.20-14-**generic** booted with Driver: "**nvidia**" without problems as did Kernel 2.6.20-**13**-386 

Has anyone else run into this or would someone else care to experiment? This would appear to be a fault in the new 386 Kernel. Then again what do I know  :) 

MSI K8n Neo - Platinum, AMD Athlon 64 3400+ 2.4Ghz, 2G ram, 2 Seagate SATA 160GB, AC'97 Audio, PNY nvidia gForce 6600 GT, blah, blah

---

### Post by Zero Prime on 2007-04-05
I had problems with mine to this afternoon.  I had to go through a lot to get it to boot and finally just uninstalled kernel 14.  It even unmounted my harddrives.

---

### Post by raptor2552 on 2007-04-05
Aw gee you didn't hafta go do that.

---

