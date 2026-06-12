---
title: "Only Wacom Touch calibrations are applied"
date: 2016-03-06
forum: General Help
---

### Post by e64462 on 2016-03-06
Hello all,

I'm using Ubuntu 15.10 on a Lenovo x61 Tablet with touch. My screen is poorly calibrated out-of-the-box, so I'd like my calibrations to persist after reboot.

_/etc/X11/xorg.conf.d/52-wacom-options.conf_ has been populated with:

```
Section "InputClass"
        # This is for human-readable purposes only.
	Identifier "wacom stylus calibration"

        # X.org detects the stylus as 'Serial Wacom Tablet' instead of 'Serial Wacom Tablet stylus'
	MatchProduct "Serial Wacom Tablet"

	Option	"TopX"		"-50"
	Option	"BottomX"	"24632"
	Option	"TopY"		"-146"
	Option	"BottomY"	"18422"
EndSection

Section "InputClass"
        # This is for human-readable purposes only.
	Identifier "wacom eraser calibration"

        # Match all devices with Wacom AND eraser in their product name
	MatchProduct "Wacom"
	MatchProduct "eraser"

	Option	"TopX"		"10"
	Option	"BottomX"	"24576"
	Option	"TopY"		"-102"
	Option	"BottomY"	"18470"
EndSection

Section "InputClass"
        # This is for human-readable purposes only.
	Identifier "wacom touch calibration"

        # Match all devices with Wacom AND touch in their product name
	MatchProduct "Wacom"	
	MatchProduct "touch"
	
	Option	"Gesture"	"True"
	Option	"TopX"		"40"
	Option	"BottomX"	"945"
	Option	"TopY"		"74"
	Option	"BottomY"	"956"
EndSection
```

The relevant portions of _Xorg.0.log_ are:

**STYLUS SECTION**
```
[     6.343] (II) config/udev: Adding input device Serial Wacom Tablet (/dev/ttyS4)
[     6.344] (**) Serial Wacom Tablet: Applying InputClass "Wacom serial class"
**[     6.344] (**) Serial Wacom Tablet: Applying InputClass "wacom stylus calibration"**
[     6.344] (II) LoadModule: "wacom"
[     6.344] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[     6.344] (II) Module wacom: vendor="X.Org Foundation"
[     6.344] 	compiled for 1.17.2, module version = 0.30.0
[     6.344] 	Module class: X.Org XInput Driver
[     6.344] 	ABI class: X.Org XInput driver, version 21.0
[     6.344] (II) wacom: Driver for Wacom graphics tablets: PenPartner, Graphire,
	Graphire2 4x5, Graphire2 5x7, Graphire3 4x5, Graphire3 6x8,
	Graphire4 4x5, Graphire4 6x8, BambooFun 4x5, BambooFun 6x8,
	Bamboo1 Medium, Graphire4 6x8 BlueTooth, CTL-460, CTH-461, CTL-660,
	CTL-461/S, Bamboo Touch, CTH-460/K, CTH-461/S, CTH-661/S1, CTH-461/L,
	CTH-661/L, Intuos 4x5, Intuos 6x8, Intuos 9x12, Intuos 12x12,
	Intuos 12x18, PTU600, PL400, PL500, PL600, PL600SX, PL550, PL800,
	PL700, PL510, PL710, DTI520, DTF720, DTF720a, DTF521, DTU1931,
	DTU2231, DTU1631, Intuos2 4x5, Intuos2 6x8, Intuos2 9x12,
	Intuos2 12x12, Intuos2 12x18, Intuos2 6x8 , Volito, PenStation,
	Volito2 4x5, Volito2 2x3, PenPartner2, Bamboo, Bamboo1, Bamboo1 4x6,
	Bamboo1 5x8, Intuos3 4x5, Intuos3 6x8, Intuos3 9x12, Intuos3 12x12,
	Intuos3 12x19, Intuos3 6x11, Intuos3 4x6, Intuos4 4x6, Intuos4 6x9,
	Intuos4 8x13, Intuos4 12x19, Intuos4 WL USB Endpoint,
	Intuos4 WL Bluetooth Endpoint, Intuos5 touch S, Intuos5 touch M,
	Intuos5 touch L, Intuos5 S, Intuos5 M, Intuos Pro S, Intuos Pro M,
	Intuos Pro L, Cintiq 21UX, Cintiq 20WSX, Cintiq 12WX, Cintiq 21UX2,
	Cintiq 24HD, Cintiq 22HD, Cintiq 24HD touch (EMR digitizer),
	Cintiq 13HD, DTK2241, DTH2242, Cintiq 22HDT, TabletPC 0x90,
	TabletPC 0x93, TabletPC 0x97, TabletPC 0x9A, CapPlus  0x9F,
	TabletPC 0xE2, TabletPC 0xE3, TabletPC 0xE5, TabletPC 0xE6,
	TabletPC 0xEC, TabletPC 0xED, TabletPC 0xEF, TabletPC 0x100,
	TabletPC 0x101, TabletPC 0x10D, TabletPC 0x116, TabletPC 0x12C,
	TabletPC 0x4001, TabletPC 0x4004, TabletPC 0x5000, TabletPC 0x5002,
	usb:172f:0024, usb:172f:0025, usb:172f:0026, usb:172f:0027,
	usb:172f:0028, usb:172f:0030, usb:172f:0031, usb:172f:0032,
	usb:172f:0033, usb:172f:0034, usb:172f:0035, usb:172f:0036,
	usb:172f:0037, usb:172f:0038, usb:172f:0039, usb:172f:0051,
	usb:172f:0052, usb:172f:0053, usb:172f:0054, usb:172f:0055,
	usb:172f:0056, usb:172f:0057, usb:172f:0058, usb:172f:0500,
	usb:172f:0501, usb:172f:0502, usb:172f:0503, usb:1b96:0001,
	usb:17ef:6004
[     6.346] (II) Using input driver 'wacom' for 'Serial Wacom Tablet'
[     6.346] (**) Serial Wacom Tablet: always reports core events
[     6.346] (**) Option "Device" "/dev/ttyS4"
[     6.347] (**) Option "StopBits" "1"
[     6.347] (**) Option "DataBits" "8"
[     6.347] (**) Option "Parity" "None"
[     6.347] (**) Option "Vmin" "1"
[     6.347] (**) Option "Vtime" "10"
[     6.347] (**) Option "FlowControl" "Xoff"
[     6.347] (II) Serial Wacom Tablet: type not specified, assuming 'stylus'.
[     6.347] (II) Serial Wacom Tablet: other types will be automatically added.
[B][     6.347] (**) Option "TopX" "-50"
[     6.347] (**) Option "TopY" "-146"
[     6.347] (**) Option "BottomX" "24632"
[     6.347] (**) Option "BottomY" "18422"[/B]
[     9.853] (WW) Serial Wacom Tablet stylus: Waited too long for answer (failed after 3 tries).
[     9.853] (II) Serial Wacom Tablet stylus: serial tablet id 0x93.
[     9.853] (--) Serial Wacom Tablet stylus: using pressure threshold of 27 for button 1
[     9.853] (--) Serial Wacom Tablet stylus: maxX=24576 maxY=18432 maxZ=255 resX=100000 resY=100000  tilt=disabled
[     9.853] (II) Serial Wacom Tablet stylus: hotplugging dependent devices.
[     9.853] (EE) Serial Wacom Tablet stylus: Invalid type 'cursor' for this device.
[     9.853] (EE) Serial Wacom Tablet stylus: Invalid type 'pad' for this device.
[     9.853] (II) Serial Wacom Tablet stylus: hotplugging completed.
[     9.853] (**) Option "config_info" "udev:/sys/devices/pnp0/00:05/tty/ttyS4"
[     9.853] (II) XINPUT: Adding extended input device "Serial Wacom Tablet stylus" (type: STYLUS, id 12)
[     9.854] (**) Serial Wacom Tablet stylus: (accel) keeping acceleration scheme 1
[     9.854] (**) Serial Wacom Tablet stylus: (accel) acceleration profile 0
[     9.854] (**) Serial Wacom Tablet stylus: (accel) acceleration factor: 2.000
[     9.854] (**) Serial Wacom Tablet stylus: (accel) acceleration threshold: 4
[     9.854] (**) Option "BaudRate" "38400"
```

**ERASER SECTION**
```
[B][     9.866] (**) Serial Wacom Tablet eraser: Applying InputClass "Wacom serial class"
[     9.866] (**) Serial Wacom Tablet eraser: Applying InputClass "wacom stylus calibration"
[     9.866] (**) Serial Wacom Tablet eraser: Applying InputClass "wacom eraser calibration"[/B]
[     9.866] (II) Using input driver 'wacom' for 'Serial Wacom Tablet eraser'
[     9.866] (**) Serial Wacom Tablet eraser: always reports core events
[     9.866] (**) Option "Device" "/dev/ttyS4"
[     9.866] (**) Option "Type" "eraser"
[     9.866] (**) Option "BaudRate" "38400"
[     9.866] (**) Option "StopBits" "1"
[     9.866] (**) Option "DataBits" "8"
[     9.866] (**) Option "Parity" "None"
[     9.866] (**) Option "Vmin" "1"
[     9.866] (**) Option "Vtime" "10"
[     9.866] (**) Option "FlowControl" "Xoff"
[B][     9.866] (**) Option "TopX" "10"
[     9.866] (**) Option "TopY" "-102"
[     9.866] (**) Option "BottomX" "24576"
[     9.866] (**) Option "BottomY" "18470"[/B]
[     9.866] (--) Serial Wacom Tablet eraser: maxX=24576 maxY=18432 maxZ=255 resX=100000 resY=100000  tilt=disabled
[     9.866] (**) Option "config_info" "udev:/sys/devices/pnp0/00:05/tty/ttyS4"
[     9.867] (II) XINPUT: Adding extended input device "Serial Wacom Tablet eraser" (type: ERASER, id 13)
[     9.867] (**) Serial Wacom Tablet eraser: (accel) keeping acceleration scheme 1
[     9.867] (**) Serial Wacom Tablet eraser: (accel) acceleration profile 0
[     9.867] (**) Serial Wacom Tablet eraser: (accel) acceleration factor: 2.000
[     9.867] (**) Serial Wacom Tablet eraser: (accel) acceleration threshold: 4
```

**TOUCH SECTION**
```
[B][     9.868] (**) Serial Wacom Tablet touch: Applying InputClass "Wacom serial class"
[     9.868] (**) Serial Wacom Tablet touch: Applying InputClass "wacom stylus calibration"
[     9.868] (**) Serial Wacom Tablet touch: Applying InputClass "wacom touch calibration"[/B]
[     9.868] (II) Using input driver 'wacom' for 'Serial Wacom Tablet touch'
[     9.868] (**) Serial Wacom Tablet touch: always reports core events
[     9.868] (**) Option "Device" "/dev/ttyS4"
[     9.868] (**) Option "Type" "touch"
[     9.868] (**) Option "BaudRate" "38400"
[     9.868] (**) Option "StopBits" "1"
[     9.868] (**) Option "DataBits" "8"
[     9.868] (**) Option "Parity" "None"
[     9.868] (**) Option "Vmin" "1"
[     9.868] (**) Option "Vtime" "10"
[     9.868] (**) Option "FlowControl" "Xoff"
[B][     9.868] (**) Option "TopX" "40"
[     9.868] (**) Option "TopY" "74"
[     9.868] (**) Option "BottomX" "945"
[     9.868] (**) Option "BottomY" "956"[/B]
[     9.868] (--) Serial Wacom Tablet touch: maxX=1024 maxY=1024 maxZ=255 resX=0 resY=0 
[     9.868] (**) Option "config_info" "udev:/sys/devices/pnp0/00:05/tty/ttyS4"
[     9.869] (II) XINPUT: Adding extended input device "Serial Wacom Tablet touch" (type: TOUCH, id 14)
[     9.869] (**) Serial Wacom Tablet touch: (accel) keeping acceleration scheme 1
[     9.869] (**) Serial Wacom Tablet touch: (accel) acceleration profile 0
[     9.869] (**) Serial Wacom Tablet touch: (accel) acceleration factor: 2.000
[     9.869] (**) Serial Wacom Tablet touch: (accel) acceleration threshold: 4
```

At this point I expect xsetwacom to report the appropriate Area for each of these devices, however after a reboot:

```
nick@notebook:~$ xsetwacom get "Serial Wacom Tablet eraser" Area
0 0 24576 18432
nick@notebook:~$ xsetwacom get "Serial Wacom Tablet stylus" Area
0 0 24576 18432
nick@notebook:~$ xsetwacom get "Serial Wacom Tablet touch" Area
40 74 945 956
```

As you can see only the touch has been calibrated. Am I doing something wrong?

---

### Post by e64462 on 2016-03-07
bump, any help?

---

### Post by e64462 on 2016-03-10
If this looks like a bug, could anyone advise which package I should file the report against?

---

### Post by sammiev on 2016-03-10
13.10 is dead, over, history.

More info [here]("http://fridge.ubuntu.com/2014/07/17/ubuntu-13-10-saucy-salamander-end-of-life-reached-on-july-17-2014/").

You will need to move to a LTS version like 12.04 or 14.04. 

15.10 is available for a short time and 16.04LTS will be released April 21.

---

### Post by e64462 on 2016-03-11
That is my mistake, I'm using 15.10. I'll edit the OP.

```
nick@notebook:~$ uname -r
4.2.0-30-generic
```

```
nick@notebook:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 15.10
Release:	15.10
Codename:	wily
```

---

### Post by e64462 on 2016-03-12
bump

---

### Post by e64462 on 2016-03-15
bump

---

