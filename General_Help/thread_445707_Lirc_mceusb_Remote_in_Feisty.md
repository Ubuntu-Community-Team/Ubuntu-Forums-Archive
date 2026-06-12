---
title: "Lirc mceusb Remote in Feisty"
date: 2007-05-16
forum: General Help
---

### Post by Mudbream on 2007-05-16
Hi,

I'm running Feisty with MythTV setup correctly for my Hauppauge WinTV HVR-1300 tv card.
The TV card came with the MCE remote ( [http://www.mythtv.org/wiki/index.php/Image:MCE-Remote-2.jpg](http://www.mythtv.org/wiki/index.php/Image:MCE-Remote-2.jpg) ).

I have followed the instruction on [https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty) exactly but when I get to the "irw" and test the remote section there is no response. It seems everything is running correctly but the remote doesn't do anything. The red light on the receiver flashes when I press the buttons on the remote but there is on response on the screen.

My "lsusb" output is:
```
lsusb
Bus 002 Device 002: ID 0471:0815 Philips
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 0bda:8187 Realtek Semiconductor Corp.
Bus 001 Device 001: ID 0000:0000

```

And "modinfo lirc_mceusb2" is 
```
modinfo lirc_mceusb2
filename:       /lib/modules/2.6.20-15-generic/misc/lirc_mceusb2.ko
license:        GPL
author:         Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
description:    Philips eHome USB IR Transciever and Microsoft MCE 2005 Remote Control driver for LIRC
srcversion:     D5478A0394C9939BFD8F8B0
alias:          usb:v045Ep00A0d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v043Ep9803d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1509p9242d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v195Dp7002d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v179Dp0010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1784p0001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v03EEp2501d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v107Bp3009d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1308pC001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1460p9150d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0609p0322d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0609p031Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p060Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p0815d*dc*dsc*dp*ic*isc*ip*
depends:        usbcore
vermagic:       2.6.20-15-generic SMP mod_unload
parm:           debug:Debug enabled or not (bool)

```

Any help regarding this would be great!
Mythtv is pretty cool but would be a lot better with the remote working!

Thanks,

Mudders

---

