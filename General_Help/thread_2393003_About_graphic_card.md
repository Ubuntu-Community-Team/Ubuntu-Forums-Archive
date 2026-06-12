---
title: "About graphic card"
date: 2018-05-28
forum: General Help
---

### Post by satimis on 2018-05-28
Hi all,

On running following command;
&#10219; cat /var/log/Xorg.0.log | grep DELL```

[     4.632] (II) NVIDIA(0): Display (DELL U2515H (DFP-1)) does not support NVIDIA 3D
[     4.639] (--) NVIDIA(0):     DELL U2515H (DFP-1) (boot, connected)
[     4.639] (--) NVIDIA(0): DELL U2515H (DFP-1): Internal TMDS
[     4.639] (--) NVIDIA(GPU-0): DELL U2515H (DFP-1): 340.0 MHz maximum pixel clock
[     4.639] (**) NVIDIA(0):     device DELL U2515H (DFP-1) (Using EDID frequencies has
[     4.640] (WW) NVIDIA(GPU-0): The EDID for DELL U2515H (DFP-1) contradicts itself: mode
[     4.640] (WW) NVIDIA(GPU-0): The EDID for DELL U2515H (DFP-1) contradicts itself: mode
[     4.640] (WW) NVIDIA(GPU-0): The EDID for DELL U2515H (DFP-1) contradicts itself: mode
[     4.640] (WW) NVIDIA(GPU-0): The EDID for DELL U2515H (DFP-1) contradicts itself: mode
[     4.640] (WW) NVIDIA(GPU-0): The EDID for DELL U2515H (DFP-1) contradicts itself: mode
[     4.640] (WW) NVIDIA(GPU-0): The EDID for DELL U2515H (DFP-1) contradicts itself: mode
[     4.641] (WW) NVIDIA(GPU-0): The EDID for DELL U2515H (DFP-1) contradicts itself: mode
[     4.641] (WW) NVIDIA(GPU-0): The EDID for DELL U2515H (DFP-1) contradicts itself: mode
[     4.641] (WW) NVIDIA(GPU-0): The EDID for DELL U2515H (DFP-1) contradicts itself: mode
[     4.641] (WW) NVIDIA(GPU-0): The EDID for DELL U2515H (DFP-1) contradicts itself: mode
[     4.641] (WW) NVIDIA(GPU-0): The EDID for DELL U2515H (DFP-1) contradicts itself: mode
[     4.641] (WW) NVIDIA(GPU-0): The EDID for DELL U2515H (DFP-1) contradicts itself: mode
[     4.641] (WW) NVIDIA(GPU-0): The EDID for DELL U2515H (DFP-1) contradicts itself: mode
[     5.424] (II) NVIDIA(GPU-0): Display (DELL U2515H (DFP-1)) does not support NVIDIA 3D
[     5.700] (II) NVIDIA(GPU-0): Display (DELL U2515H (DFP-1)) does not support NVIDIA 3D
[    16.655] (II) NVIDIA(GPU-0): Display (DELL U2515H (DFP-1)) does not support NVIDIA 3D
[    17.045] (II) NVIDIA(GPU-0): Display (DELL U2515H (DFP-1)) does not support NVIDIA 3D
[    18.147] (II) NVIDIA(GPU-0): Display (DELL U2515H (DFP-1)) does not support NVIDIA 3D
[    39.485] (II) NVIDIA(GPU-0): Display (DELL U2515H (DFP-1)) does not support NVIDIA 3D

```
I found **"Display (DELL U2515H (DFP-1)) does not support NVIDIA 3D"**

Is my graphic card getting old?  It has been used for about 10 years.  However there is nothing wrong on the monitor screen.

According to my recollection it has happened before.  I left it untouched then it becomes normal.

Please advise.  Thanks

Regards
satimis

---

### Post by Yellow Pasque on 2018-05-28
It looks like the message might be cut off. Googling shows the message is probably "does not support NVIDIA 3D **Vision**"

---

### Post by satimis on 2018-05-28
> **Temüjin said:**
> It looks like the message might be cut off. Googling shows the message is probably "does not support NVIDIA 3D **Vision**"
Yes, you're correct.

&#10219; tail /var/log/Xorg.0.log```

[     5.700] (II) NVIDIA(GPU-0): Display (DELL U2515H (DFP-1)) does not support NVIDIA 3D
[     5.700] (II) NVIDIA(GPU-0):     Vision stereo.
[    16.655] (II) NVIDIA(GPU-0): Display (DELL U2515H (DFP-1)) does not support NVIDIA 3D
[    16.655] (II) NVIDIA(GPU-0):     Vision stereo.
[    17.045] (II) NVIDIA(GPU-0): Display (DELL U2515H (DFP-1)) does not support NVIDIA 3D
[    17.045] (II) NVIDIA(GPU-0):     Vision stereo.
[    18.147] (II) NVIDIA(GPU-0): Display (DELL U2515H (DFP-1)) does not support NVIDIA 3D
[    18.147] (II) NVIDIA(GPU-0):     Vision stereo.
[    39.485] (II) NVIDIA(GPU-0): Display (DELL U2515H (DFP-1)) does not support NVIDIA 3D
[    39.485] (II) NVIDIA(GPU-0):     Vision stereo.

```

Thanks

Regards
satimis

---

### Post by Yellow Pasque on 2018-05-28
Please mark the thread solved unless you have further questions.

---

