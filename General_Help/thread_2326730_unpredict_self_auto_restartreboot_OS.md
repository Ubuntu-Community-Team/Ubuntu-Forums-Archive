---
title: "unpredict self auto restart/reboot OS"
date: 2016-06-04
forum: General Help
---

### Post by satimis on 2016-06-04
Hi all.

Ubuntu 14.04 desktop
Display - Dell UltraSharp U2515H (newly installed)

Recently I have encountered problem of self restart/reboot while working.  I couldn't predict when it'll happen.  Occasionally a click on mouse while working will initiate restart/reboot the OS.

I have been searching on Internet and couldn't find a solution there. This problem started after installing the new DELL display.  However the new display is working correctly without problem.

On terminal running;

&#10219; cat /var/log/Xorg.0.log | grep DELL```

[     8.188] (II) NVIDIA(0): Display (DELL U2515H (DFP-1)) does not support NVIDIA 3D
[     8.199] (--) NVIDIA(0):     DELL U2515H (DFP-1) (boot, connected)
[     8.199] (--) NVIDIA(0): DELL U2515H (DFP-1): Internal TMDS
[     8.199] (--) NVIDIA(GPU-0): DELL U2515H (DFP-1): 340.0 MHz maximum pixel clock
[     8.199] (**) NVIDIA(0):     device DELL U2515H (DFP-1) (Using EDID frequencies has
[     8.199] (WW) NVIDIA(GPU-0): The EDID for DELL U2515H (DFP-1) contradicts itself: mode
[     8.200] (WW) NVIDIA(GPU-0): The EDID for DELL U2515H (DFP-1) contradicts itself: mode
[     8.200] (WW) NVIDIA(GPU-0): The EDID for DELL U2515H (DFP-1) contradicts itself: mode
[     8.200] (WW) NVIDIA(GPU-0): The EDID for DELL U2515H (DFP-1) contradicts itself: mode
[     8.200] (WW) NVIDIA(GPU-0): The EDID for DELL U2515H (DFP-1) contradicts itself: mode
[     8.200] (WW) NVIDIA(GPU-0): The EDID for DELL U2515H (DFP-1) contradicts itself: mode
[     8.200] (WW) NVIDIA(GPU-0): The EDID for DELL U2515H (DFP-1) contradicts itself: mode
[     8.200] (WW) NVIDIA(GPU-0): The EDID for DELL U2515H (DFP-1) contradicts itself: mode
[     8.200] (WW) NVIDIA(GPU-0): The EDID for DELL U2515H (DFP-1) contradicts itself: mode
[     8.200] (WW) NVIDIA(GPU-0): The EDID for DELL U2515H (DFP-1) contradicts itself: mode
[     8.200] (WW) NVIDIA(GPU-0): The EDID for DELL U2515H (DFP-1) contradicts itself: mode
[     8.200] (WW) NVIDIA(GPU-0): The EDID for DELL U2515H (DFP-1) contradicts itself: mode
[     8.201] (WW) NVIDIA(GPU-0): The EDID for DELL U2515H (DFP-1) contradicts itself: mode
[     8.705] (II) NVIDIA(GPU-0): Display (DELL U2515H (DFP-1)) does not support NVIDIA 3D
[     8.956] (II) NVIDIA(GPU-0): Display (DELL U2515H (DFP-1)) does not support NVIDIA 3D
[    15.954] (II) NVIDIA(GPU-0): Display (DELL U2515H (DFP-1)) does not support NVIDIA 3D
[    16.129] (II) NVIDIA(GPU-0): Display (DELL U2515H (DFP-1)) does not support NVIDIA 3D
[    17.112] (II) NVIDIA(GPU-0): Display (DELL U2515H (DFP-1)) does not support NVIDIA 3D
[    17.214] (II) NVIDIA(GPU-0): Display (DELL U2515H (DFP-1)) does not support NVIDIA 3D
[    32.677] (II) NVIDIA(GPU-0): Display (DELL U2515H (DFP-1)) does not support NVIDIA 3D
[    37.810] (II) NVIDIA(GPU-0): Display (DELL U2515H (DFP-1)) does not support NVIDIA 3D

```

Would it matter?  Please help.  Thanks

Regards
satimis

---

### Post by ventrical on 2016-06-04
Are you using nVidia proprietary drivers or nouveau?

You might have to remove and reinstall drivers. That may work. 

or you can even try recovery mode from GRuB and see if that corrects.

Regards..

---

### Post by satimis on 2016-06-04
> **ventrical said:**
> Are you using nVidia proprietary drivers or nouveau?

You might have to remove and reinstall drivers. That may work. 

or you can even try recovery mode from GRuB and see if that corrects.

Regards..

Hi,

Thanks for your reply.

This Ubuntu box, which is running Oracle VirtualBox, has been running several years.  I couldn't recall the type of driver installed previously.  Could you please shed me some light where to start and how to fix the problem?  Thanks

Regards
satimis

---

