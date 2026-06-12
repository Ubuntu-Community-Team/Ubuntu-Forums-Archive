---
title: "volume"
date: 2006-08-17
forum: General Help
---

### Post by hemple on 2006-08-17
linux was just put on my laptop a couple days ago. windows volume was perfect. but now its very low. and when i try to turn it up through the music player...it gets distorted. any ideas?

---

### Post by jr.gotti on 2006-08-17
h-e-e-e-e-e-e-e-e-e-e-e-m-p!

First off, very descriptive title. I'm sure that will attract a lot of attention...:P

And now that I think about it, it might be a driver thing...

How about putting your "lspci" output in here...

-G-o-o-o-o-o-o-o-o-o-o-t-t-t-t-i-i-i-i

---

### Post by Greycloak on 2006-08-17
In a terminal window type:

```
alsamixer
```

The 'master' channel is the same as the volume slider.  Try playing around with different levels for 'PCM'

---

### Post by hemple on 2006-08-17
hey thanks man. im new at the linux game. the pcm is at 100. volume just goes down from there. my friend told me to enter lspci...this is the output. thanks again



0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Graphics Port (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
0000:00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
0000:00:1f.2 0106: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=AHCI (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0398 (rev a1)
0000:06:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)0000:08:06.0 CardBus bridge: Texas Instruments: Unknown device 8039
0000:08:06.1 FireWire (IEEE 1394): Texas Instruments: Unknown device 803a
0000:08:06.2 Mass storage controller: Texas Instruments: Unknown device 803b
0000:08:06.3 0805: Texas Instruments: Unknown device 803c
0000:08:08.0 Ethernet controller: Intel Corporation: Unknown device 1092 (rev 01)

---

