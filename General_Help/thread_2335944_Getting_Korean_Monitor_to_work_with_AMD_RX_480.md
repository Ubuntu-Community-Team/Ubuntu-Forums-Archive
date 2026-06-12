---
title: "Getting Korean Monitor to work with AMD RX 480"
date: 2016-09-02
forum: General Help
---

### Post by ninjapepper707 on 2016-09-02
Hi I recently just upgraded to a Sapphire Radeon RX 480 from a Nvidia Card. I'm using the AMDGPU-PRO drivers from AMD's website.  I also have a Qnix 1440p 27" korean monitor which if plugged in will freeze at start up. When I had my Nvidia card installed I would just edit it's xorg.conf file and add the underlined part shown below:
 [B][FONT=Courier New]
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
[/FONT][/B][B][B]_[FONT=Courier New]Option         "IgnoreEDIDChecksum" "DFP"[/FONT]_
**[FONT=Courier New]EndSection[/FONT]**[/B][/B]

This would fix all the problems associated with the monitor. Now my question is how would I accomplish this with my new RX480 card? Can I create a xorg.conf file with AMDGPU-PRO drivers or where is it's configuration file?  Sorry I'm still a little new to linux but i've been searching all morning trying to figure this out any help would be much appreciative thanks!

---

