---
title: "VDPAU nvidia errors"
date: 2017-02-12
forum: General Help
---

### Post by fizikz on 2017-02-12
I recently upgraded to Ubuntu 16.04 (using MATE desktop environment) and now vdpau is not working, with errors given when using mplayer, vlc, kodi, etc.

```
$ vdpauinfo
display: :0   screen: 0
VDPAU capture: Enabled
vdp_imp_device_create_x11(0x9871a10, 0, -, -)
VDPAU nvidia: Version: NVIDIA VDPAU Driver Shared Library  304.134  Fri Dec  9 12:12:23 PST 2016
VDPAU nvidia: Error detected 10 227  5
VDPAU nvidia: Backtrace:
    -> 1
Error creating VDPAU device: 1

```

In mplayer, with similar messages in vlc:
```
VDPAU capture: Enabled
vdp_imp_device_create_x11(0x810fc488, 0, -, -)
VDPAU nvidia: Version: NVIDIA VDPAU Driver Shared Library  304.134  Fri Dec  9 12:12:23 PST 2016
VDPAU nvidia: Error detected 10 227  5
VDPAU nvidia: Backtrace:
    -> 1
[vdpau] Error when calling vdp_device_create_x11: 1

```

When starting kodi:
```
libEGL warning: DRI2: failed to authenticate

```

I tried googling for solutions with no luck. Any suggestions?

---

### Post by mc4man on 2017-02-12
Try reinstalling the Nvidia drivers or if your hardware supports  install a newer version as 304 are pretty old

---

### Post by fizikz on 2017-02-12
What's the best way to reinstall the Nvidia drivers?

I tried using the Additional Drivers dialog to switch to nouveau drivers (vdpauinfo still resulted in an error, although different), then switching back to nvidia drivers. Still the same error.

The graphics card is a Go7700 which is supported only by legacy drivers. Version 304.134 is currently the most recent legacy driver.

I also tried switching between no compositing and Marco+Compton; no difference.

---

### Post by fizikz on 2017-02-12
I just realized that VDPAU is not supported by my hardware. According to Wikipedia, VDPAU works for GeForce 8 Series cards and later: [https://en.wikipedia.org/wiki/Nvidia_PureVideo#Table_of_GPUs_containing_a_PureVideo_SIP_block](https://en.wikipedia.org/wiki/Nvidia_PureVideo#Table_of_GPUs_containing_a_PureVideo_SIP_block)

---

