---
title: "fglrx giving me horrible problems"
date: 2007-05-15
forum: General Help
---

### Post by sarixe on 2007-05-15
recently, fglrx stopped functioning with 3d, for no apparent reason.  here's what i was able to gather:

```

$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

```

---

### Post by NT4usB on 2007-05-15
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by sarixe on 2007-05-22
nothing different.  here's what else i found, highlighting relevant pieces to save space:

/etc/X11/xorg.conf:
```
Section "Device"
	Identifier	"ATI Radeon Xpress 200 Series"
	Driver	"fglrx"
	Option	"VideoOverlay" "on"
	Option	"OpenGLOverlay" "off"
	BusID		"PCI:1:05:0"
EndSection
...
Section "Extensions"
	Option "Composite" "Disable"
EndSection
```

/var/log/Xorg.0.log:
```
(II) PCI: 01:05:0: chip 1002,5974 card a0a0,0565 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:05:1: chip 1002,5874 card a0a0,0564 rev 00 class 03,80,00 hdr 00
...
(--) PCI:*(1:5:0) ATI Technologies Inc RS482 [Radeon Xpress 200] rev 0, Mem @ 0xd0000000/28, 0xfdaf0000/16, I/O @ 0xee00/8
(--) PCI: (1:5:1) ATI Technologies Inc unknown chipset (0x5874) rev 0, Mem @ 0xfda20000/16
...
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.36.5
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
...
(II) ATI Proprietary Linux Driver Version Identifier:8.36.5
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.36g1                           
(II) ATI Proprietary Linux Driver Build Date: Apr 17 2007 10:04:24
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.36.1.1.2.3-driver-lnx-x86-x86_64-338188
(WW) fglrx: No matching Device section for instance (BusID PCI:1:5:1) found
(--) Chipset Supported AMD Graphics Processor (0x5974) found
...
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
(WW) fglrx(0): Failed to open DRM connection
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
...
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(EE) fglrx(0): GART is not initialized, disabling DRI
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

```
What seems to be happening is that xorg is configured correctly, and recognizes it, but then randomly switches over to the wrong PCI bus address.  This results in a complete failure for DRI and DRM.  It seems to happen with even the open source driver, so i know it's not fglrx's fault.  any help?

---

### Post by NT4usB on 2007-05-22
Did you google:
`GART is not initialized, disabling DRI`

---

