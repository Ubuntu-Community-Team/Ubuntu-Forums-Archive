---
title: "Mouse turning off/on"
date: 2007-07-11
forum: General Help
---

### Post by gav616 on 2007-07-11
my mouse keeps turning off then on, usually when using it heavily i.e. in games or Firefox window switching (fast graphics)
or just sometimes randomly.

ive updated my firmware but its still the same, changing usb port delays the problem for abit but it comes back.

TBH it might be that my mouse is just funked.. but lets assume its buntu for now

i'm getting errors when its on/off,

debug
```
Jul 11 15:35:11 localhost NetworkManager: <debug info>^I[1184164511.535247] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_425_ff07_noserial'). 
Jul 11 15:35:11 localhost NetworkManager: <debug info>^I[1184164511.584181] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_425_ff07_noserial_if0'). 
Jul 11 15:35:11 localhost NetworkManager: <debug info>^I[1184164511.595907] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_425_ff07_noserial_usbraw'). 
Jul 11 15:35:50 localhost NetworkManager: <debug info>^I[1184164550.667107] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_425_ff07_noserial_if0'). 
Jul 11 15:35:50 localhost NetworkManager: <debug info>^I[1184164550.670459] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_425_ff07_noserial_usbraw'). 
Jul 11 15:35:50 localhost NetworkManager: <debug info>^I[1184164550.673279] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_425_ff07_noserial'). 
Jul 11 15:35:56 localhost NetworkManager: <debug info>^I[1184164556.236735] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1532_101_noserial'). 
Jul 11 15:35:56 localhost NetworkManager: <debug info>^I[1184164556.282865] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial'). 
Jul 11 15:35:57 localhost NetworkManager: <debug info>^I[1184164557.705462] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1532_101_noserial_if1'). 
Jul 11 15:35:57 localhost NetworkManager: <debug info>^I[1184164557.757352] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1532_101_noserial_usbraw'). 
Jul 11 15:35:57 localhost NetworkManager: <debug info>^I[1184164557.761266] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_logicaldev_input'). 
Jul 11 15:35:57 localhost NetworkManager: <debug info>^I[1184164557.779029] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1532_101_noserial_if1_logicaldev_input'). 
Jul 11 15:53:16 localhost NetworkManager: <debug info>^I[1184165596.667372] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_logicaldev_input'). 
Jul 11 15:53:16 localhost NetworkManager: <debug info>^I[1184165596.669166] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial'). 
Jul 11 15:53:16 localhost NetworkManager: <debug info>^I[1184165596.777374] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1532_101_noserial_if1_logicaldev_input'). 
Jul 11 15:53:16 localhost NetworkManager: <debug info>^I[1184165596.779527] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1532_101_noserial_if1'). 
Jul 11 15:53:16 localhost NetworkManager: <debug info>^I[1184165596.783678] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1532_101_noserial'). 
Jul 11 15:53:16 localhost NetworkManager: <debug info>^I[1184165596.826664] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1532_101_noserial_usbraw'). 
Jul 11 15:53:17 localhost NetworkManager: <debug info>^I[1184165597.522523] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1532_101_noserial'). 
Jul 11 15:53:17 localhost NetworkManager: <debug info>^I[1184165597.699533] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial'). 
Jul 11 15:53:18 localhost NetworkManager: <debug info>^I[1184165598.983680] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_logicaldev_input'). 
Jul 11 15:53:19 localhost NetworkManager: <debug info>^I[1184165599.096420] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1532_101_noserial_if1'). 
Jul 11 15:53:19 localhost NetworkManager: <debug info>^I[1184165599.145199] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1532_101_noserial_usbraw'). 
Jul 11 15:53:19 localhost NetworkManager: <debug info>^I[1184165599.175251] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1532_101_noserial_if1_logicaldev_input'). 
Jul 11 15:53:49 localhost NetworkManager: <debug info>^I[1184165629.386508] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_logicaldev_input'). 
Jul 11 15:53:49 localhost NetworkManager: <debug info>^I[1184165629.388261] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial'). 
Jul 11 15:53:49 localhost NetworkManager: <debug info>^I[1184165629.441920] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1532_101_noserial_if1_logicaldev_input'). 
Jul 11 15:53:49 localhost NetworkManager: <debug info>^I[1184165629.444034] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1532_101_noserial_if1'). 
Jul 11 15:53:49 localhost NetworkManager: <debug info>^I[1184165629.447527] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1532_101_noserial_usbraw'). 
Jul 11 15:53:49 localhost NetworkManager: <debug info>^I[1184165629.450990] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1532_101_noserial'). 
Jul 11 15:53:50 localhost NetworkManager: <debug info>^I[1184165630.612824] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1532_101_noserial'). 
Jul 11 15:53:50 localhost NetworkManager: <debug info>^I[1184165630.658136] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial'). 
Jul 11 15:53:52 localhost NetworkManager: <debug info>^I[1184165632.062887] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1532_101_noserial_if1'). 
Jul 11 15:53:52 localhost NetworkManager: <debug info>^I[1184165632.114347] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1532_101_noserial_usbraw'). 
Jul 11 15:53:52 localhost NetworkManager: <debug info>^I[1184165632.118247] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_logicaldev_input'). 
Jul 11 15:53:52 localhost NetworkManager: <debug info>^I[1184165632.135974] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1532_101_noserial_if1_logicaldev_input'). 
```

kern.log
```
Jul 11 13:57:06 localhost kernel: [   48.056479] [fglrx] free       GART = 51113984
Jul 11 13:57:06 localhost kernel: [   48.056481] [fglrx] max single GART = 51113984
Jul 11 13:57:06 localhost kernel: [   48.056483] [fglrx] total      LFB  = 134217728
Jul 11 13:57:06 localhost kernel: [   48.056484] [fglrx] free       LFB  = 116387840
Jul 11 13:57:06 localhost kernel: [   48.056486] [fglrx] max single LFB  = 116387840
Jul 11 13:57:06 localhost kernel: [   48.056488] [fglrx] total      Inv  = 134217728
Jul 11 13:57:06 localhost kernel: [   48.056490] [fglrx] free       Inv  = 134217728
Jul 11 13:57:06 localhost kernel: [   48.056491] [fglrx] max single Inv  = 134217728
Jul 11 13:57:06 localhost kernel: [   48.056493] [fglrx] total      TIM  = 0
Jul 11 15:34:30 localhost kernel: [ 5887.873422] drivers/usb/input/hid-core.c: input irq status -75 received
Jul 11 15:34:58 localhost kernel: [ 5916.161303] usb 1-1: USB disconnect, address 4
Jul 11 15:35:11 localhost kernel: [ 5929.059794] usb 1-1: new full speed USB device using ohci_hcd and address 5
Jul 11 15:35:11 localhost kernel: [ 5929.254773] usb 1-1: configuration #1 chosen from 1 choice
Jul 11 15:35:50 localhost kernel: [ 5968.355490] usb 1-1: USB disconnect, address 5
Jul 11 15:35:56 localhost kernel: [ 5973.707070] usb 1-1: new full speed USB device using ohci_hcd and address 6
Jul 11 15:35:56 localhost kernel: [ 5973.921015] usb 1-1: configuration #1 chosen from 1 choice
Jul 11 15:35:57 localhost kernel: [ 5975.258995] input: Razer Razer Copperhead Laser Mouse as /class/input/input5
Jul 11 15:35:57 localhost kernel: [ 5975.259050] input: USB HID v10.01 Mouse [Razer Razer Copperhead Laser Mouse] on usb-0000:00:02.0-1
Jul 11 15:35:57 localhost kernel: [ 5975.265056] input: Razer Razer Copperhead Laser Mouse as /class/input/input6
Jul 11 15:35:57 localhost kernel: [ 5975.265084] input: USB HID v10.01 Keyboard [Razer Razer Copperhead Laser Mouse] on usb-0000:00:02.0-1
Jul 11 15:36:17 localhost kernel: [ 5994.872002] drivers/usb/input/hid-core.c: input irq status -75 received
Jul 11 15:53:16 localhost kernel: [ 7013.740031] usb 1-1: USB disconnect, address 6
Jul 11 15:53:17 localhost kernel: [ 7014.394547] usb 1-1: new full speed USB device using ohci_hcd and address 7
Jul 11 15:53:17 localhost kernel: [ 7014.600847] usb 1-1: configuration #1 chosen from 1 choice
Jul 11 15:53:18 localhost kernel: [ 7015.938812] input: Razer Razer Copperhead Laser Mouse as /class/input/input7
Jul 11 15:53:18 localhost kernel: [ 7015.938866] input: USB HID v10.01 Mouse [Razer Razer Copperhead Laser Mouse] on usb-0000:00:02.0-1
Jul 11 15:53:18 localhost kernel: [ 7015.944859] input: Razer Razer Copperhead Laser Mouse as /class/input/input8
Jul 11 15:53:18 localhost kernel: [ 7015.944889] input: USB HID v10.01 Keyboard [Razer Razer Copperhead Laser Mouse] on usb-0000:00:02.0-1
Jul 11 15:53:49 localhost kernel: [ 7046.443935] hub 1-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
Jul 11 15:53:49 localhost kernel: [ 7046.443942] usb 1-1: USB disconnect, address 7
Jul 11 15:53:50 localhost kernel: [ 7047.455029] usb 1-1: new full speed USB device using ohci_hcd and address 9
Jul 11 15:53:50 localhost kernel: [ 7047.661087] usb 1-1: configuration #1 chosen from 1 choice
Jul 11 15:53:51 localhost kernel: [ 7048.999054] input: Razer Razer Copperhead Laser Mouse as /class/input/input9
Jul 11 15:53:51 localhost kernel: [ 7048.999108] input: USB HID v10.01 Mouse [Razer Razer Copperhead Laser Mouse] on usb-0000:00:02.0-1
Jul 11 15:53:51 localhost kernel: [ 7049.005106] input: Razer Razer Copperhead Laser Mouse as /class/input/input10
Jul 11 15:53:51 localhost kernel: [ 7049.005135] input: USB HID v10.01 Keyboard [Razer Razer Copperhead Laser Mouse] on usb-0000:00:02.0-1
```

syslog
```
Jul 11 15:53:16 localhost NetworkManager: <debug info>^I[1184165596.783678] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1532_101_noserial'). 
Jul 11 15:53:16 localhost NetworkManager: <debug info>^I[1184165596.826664] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1532_101_noserial_usbraw'). 
Jul 11 15:53:17 localhost kernel: [ 7014.394547] usb 1-1: new full speed USB device using ohci_hcd and address 7
Jul 11 15:53:17 localhost NetworkManager: <debug info>^I[1184165597.522523] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1532_101_noserial'). 
Jul 11 15:53:17 localhost kernel: [ 7014.600847] usb 1-1: configuration #1 chosen from 1 choice
Jul 11 15:53:17 localhost NetworkManager: <debug info>^I[1184165597.699533] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial'). 
Jul 11 15:53:18 localhost kernel: [ 7015.938812] input: Razer Razer Copperhead Laser Mouse as /class/input/input7
Jul 11 15:53:18 localhost kernel: [ 7015.938866] input: USB HID v10.01 Mouse [Razer Razer Copperhead Laser Mouse] on usb-0000:00:02.0-1
Jul 11 15:53:18 localhost kernel: [ 7015.944859] input: Razer Razer Copperhead Laser Mouse as /class/input/input8
Jul 11 15:53:18 localhost kernel: [ 7015.944889] input: USB HID v10.01 Keyboard [Razer Razer Copperhead Laser Mouse] on usb-0000:00:02.0-1
Jul 11 15:53:18 localhost NetworkManager: <debug info>^I[1184165598.983680] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_logicaldev_input'). 
Jul 11 15:53:19 localhost NetworkManager: <debug info>^I[1184165599.096420] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1532_101_noserial_if1'). 
Jul 11 15:53:19 localhost NetworkManager: <debug info>^I[1184165599.145199] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1532_101_noserial_usbraw'). 
Jul 11 15:53:19 localhost NetworkManager: <debug info>^I[1184165599.175251] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1532_101_noserial_if1_logicaldev_input'). 
Jul 11 15:53:49 localhost kernel: [ 7046.443935] hub 1-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
Jul 11 15:53:49 localhost kernel: [ 7046.443942] usb 1-1: USB disconnect, address 7
Jul 11 15:53:49 localhost NetworkManager: <debug info>^I[1184165629.386508] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_logicaldev_input'). 
Jul 11 15:53:49 localhost NetworkManager: <debug info>^I[1184165629.388261] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial'). 
Jul 11 15:53:49 localhost NetworkManager: <debug info>^I[1184165629.441920] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1532_101_noserial_if1_logicaldev_input'). 
Jul 11 15:53:49 localhost NetworkManager: <debug info>^I[1184165629.444034] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1532_101_noserial_if1'). 
Jul 11 15:53:49 localhost NetworkManager: <debug info>^I[1184165629.447527] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1532_101_noserial_usbraw'). 
Jul 11 15:53:49 localhost NetworkManager: <debug info>^I[1184165629.450990] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1532_101_noserial'). 
Jul 11 15:53:50 localhost kernel: [ 7047.455029] usb 1-1: new full speed USB device using ohci_hcd and address 9
Jul 11 15:53:50 localhost NetworkManager: <debug info>^I[1184165630.612824] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1532_101_noserial'). 
Jul 11 15:53:50 localhost kernel: [ 7047.661087] usb 1-1: configuration #1 chosen from 1 choice
Jul 11 15:53:50 localhost NetworkManager: <debug info>^I[1184165630.658136] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial'). 
Jul 11 15:53:51 localhost kernel: [ 7048.999054] input: Razer Razer Copperhead Laser Mouse as /class/input/input9
Jul 11 15:53:51 localhost kernel: [ 7048.999108] input: USB HID v10.01 Mouse [Razer Razer Copperhead Laser Mouse] on usb-0000:00:02.0-1
Jul 11 15:53:51 localhost kernel: [ 7049.005106] input: Razer Razer Copperhead Laser Mouse as /class/input/input10
Jul 11 15:53:51 localhost kernel: [ 7049.005135] input: USB HID v10.01 Keyboard [Razer Razer Copperhead Laser Mouse] on usb-0000:00:02.0-1
Jul 11 15:53:52 localhost NetworkManager: <debug info>^I[1184165632.062887] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1532_101_noserial_if1'). 
Jul 11 15:53:52 localhost NetworkManager: <debug info>^I[1184165632.114347] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1532_101_noserial_usbraw'). 
Jul 11 15:53:52 localhost NetworkManager: <debug info>^I[1184165632.118247] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_logicaldev_input'). 
Jul 11 15:53:52 localhost NetworkManager: <debug info>^I[1184165632.135974] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1532_101_noserial_if1_logicaldev_input'). 
Jul 11 15:54:44 localhost ntpd[4663]: adjusting local clock by -0.225044s
Jul 11 16:02:04 localhost ntpd[4663]: adjusting local clock by -0.156886s
```

xorg.conf for my mouse
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device" "/dev/input/mice"
	Option		"Buttons" "7"
	Option		"ZAxisMapping" "4 5"
	Option		"ButtonMapping" "1 2 3 6 7"
	Option		"Emulate3Buttons" "false"
	Option		"Resolution" "2000"
    	Option		"SampleRate" "1000"
EndSection
```

---

### Post by gav616 on 2007-07-11
bump.

am getting that freedesktop debug info on a few things, 

i.e.

i put a dvd in and getting hal freedesktop log flood for usb device.. which is obvious my mouse..

does any 1 thing its got to do with xorg not liking a high mouse DPI / resolution? which is interfering with I/O?

these are only massive guesses...

---

### Post by gav616 on 2007-07-12
its getting worse help?!

---

### Post by christhemonkey on 2007-07-12
I'd say your mouse is foobared.
Try using it on a different pc see if it works there?

---

