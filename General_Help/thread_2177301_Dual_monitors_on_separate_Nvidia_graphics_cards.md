---
title: "Dual monitors on separate Nvidia graphics cards"
date: 2013-09-28
forum: General Help
---

### Post by JoinTheRealms on 2013-09-28
Hey guys

Im having an issue with dual displays on Ubuntu 13.04

I have a 50in tv as display 1 and a 1920x1200 montior as display 2 both are using mini to hdmi connections
I have two gtx570s with 310 proprietary nvidia driver. 

Im trying to extend these monitors, but cant in my current configuration. display 1 is connected to gpu0 with hdmi and display 2 is connected to gpu1 with hdmi.
Display 2 refuses to extend, it wont even apper in the gnome display settings. NVIDIA X Server Settings sees the monitor connected on gpu1 but no configuration works, changing xserver settings appers to do nothing. This same setup is working fine in Windows 8.

My setup does work if i connect display 2 via VGA to gpu0 (so both displays are connected to one gpu) But this is not ideal, as it creates alot of heat on the one gpu.

I guess what im asking is with the current nvidia drivers is it possible to have two displays connected to two separate graphics cards? Ive also tried the latest 319 driver from nvidias website but it wouldnt start xerver so i fell back to 310. 

Thanks guys :)

---

