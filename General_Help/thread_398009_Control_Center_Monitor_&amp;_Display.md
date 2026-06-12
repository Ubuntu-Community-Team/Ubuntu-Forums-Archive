---
title: "Control Center: Monitor &amp; Display"
date: 2007-03-31
forum: General Help
---

### Post by dreadlord_chris on 2007-03-31
The Hardware tab of the Monitor & Display section is showing Driver as **nv** when, in fact, I'm using the **nvidia** driver.

```

chris@HAL421:~$ modprobe -l nv*
/lib/modules/2.6.20-13-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/2.6.20-13-generic/kernel/drivers/char/nvram.ko
/lib/modules/2.6.20-13-generic/kernel/drivers/char/agp/nvidia-agp.ko
/lib/modules/2.6.20-13-generic/volatile/nvidia.ko
/lib/modules/2.6.20-13-generic/volatile/nvidia_legacy.ko
chris@HAL421:~$

```

xorg.conf:
```

Section "Device"
        Identifier      "NVIDIA GeForce 7300LE"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "UseFBDev"              "true"
        Option          "AddARGBVisuals"                "True"
        Option          "NoLogo"                "True"
        Option          "XAANoOffscreenPixmaps" "true"
EndSection

```

Also, the Size, Orientation & Postitioning tab shows the correct resolution but the refresh rate is incorrect. My refresh is 60Hz, the applet shows 50Hz - with the only 2 other options being 53Hz & 54Hz.

System:
Intel(R) Celeron(R) D CPU 3.20GHz
NVIDIA GeForce 7300LE 128MB
HP vs15c LCD Monitor

---

### Post by acormack on 2007-04-01
what makes you think this isn't the nvidia driver?

/lib/modules/2.6.20-13-generic/volatile/nvidia.ko

---

### Post by dreadlord_chris on 2007-04-01
> **acormack said:**
> what makes you think this isn't the nvidia driver?

/lib/modules/2.6.20-13-generic/volatile/nvidia.ko

there are 2 NVIDIA drivers. There's the **free** one, in the repositories - it's labled **nv**. Then there's the **proprietary** driver, the one you download from NVIDIA - the one I'm using, it's labled **nividia**

That module line shows that my kernel has loaded the *proprietary* driver - which is what I expect and is correct.

The Monitor & Display applet shows the _free, open-source_ driver - this is **not** correct.

My point is that the Monitor & Display applet is not showing the current config correctly...

---

### Post by acormack on 2007-04-01
If you go into adminstrator mode can't you change it?

---

### Post by dreadlord_chris on 2007-04-01
> **acormack said:**
> If you go into adminstrator mode can't you change it?

yes I can - not the point though

---

