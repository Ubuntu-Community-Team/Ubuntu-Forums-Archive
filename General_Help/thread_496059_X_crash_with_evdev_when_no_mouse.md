---
title: "X crash with evdev when no mouse"
date: 2007-07-08
forum: General Help
---

### Post by Toufik on 2007-07-08
Hi,

I have a USB Logitech mouse with 7 buttons (3 + wheel up/down + wheel left/right). So I change my Xorg.conf to be able to use all these buttons:
```

#Section "InputDevice"
#       Identifier      "Configured Mouse"
#       Driver          "mouse"
#       Option          "CorePointer"
#       Option          "Device"                "/dev/input/mice"
#       Option          "Protocol"              "ImPS/2"
#       Option          "ZAxisMapping"          "4 5"
#       Option          "Emulate3Buttons"       "true"
#EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "evdev"
        Option          "CorePointer"
        Option          "Name"  "Logitech USB Optical Mouse"
EndSection

```

It works ! So easy :)

Until I reboot with the mouse **unplugged**. The X server crashed!

Here is the relevant part of /var/log/Xorg.0.log
```

...
(II) evdev brain: Rescanning devices (1).
(EE) PreInit returned NULL for "Configured Mouse"
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event6
(**) Option "Device" "/dev/input/event6"
(**) Option "SHMConfig" "true"
(**) Option "HorizScrollDelta" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(WW) <default pointer>: No Device specified, looking for one...
(II) <default pointer>: Setting Device option to "/dev/input/mice"
(--) <default pointer>: Device: "/dev/input/mice"
(==) <default pointer>: Protocol: "Auto"
(**) Option "AlwaysCore"
(**) <default pointer>: always reports core events
(==) <default pointer>: Emulate3Buttons, Emulate3Timeout: 50
(**) <default pointer>: ZAxisMapping: buttons 4 and 5
(**) <default pointer>: Buttons: 9
(WW) No core pointer registered
(II) XINPUT: Adding extended input device "<default pointer>" (type: MOUSE)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "evdev brain" (type: evdev brain)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
Synaptics DeviceInit called
SynapticsCtrl called.
(II) evdev brain: Rescanning devices (2).
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event6
(**) Option "Device" "/dev/input/event6"
(--) Synaptics Touchpad touchpad found
(--) <default pointer>: PnP-detected protocol: "ExplorerPS/2"
(II) <default pointer>: ps2EnableDataReporting: succeeded
No core pointer

Fatal server error:
failed to initialize core devices

```

The evdev documentation is not really wonderful :) and I don't see how to fix it

Any idea?

---

### Post by kidders on 2007-07-09
Hi there,

I may be misunderstanding, but there isn't really anything to fix. Xorg won't start without at least one pointing device.

---

### Post by Toufik on 2007-07-10
I understand I need a pointer but then why my synaptic touchpad is not enough?

With the "mouse" driver when no mouse is connected, xorg starts normally

With the "evdev" driver and no mouse, xorg crashes. With the mouse plugged, once xorg is started, I can unplug it and touchpad works correctly.

For me, something has to be fixed since the mouse has only to be present at X start ! If somecone with the evdev driver could try this also in order to see if the porblem comes from my laptop or from the driver.

Thanks

---

### Post by kidders on 2007-07-10
Ahh... I think I see what you mean. Try thinking of things in terms of /dev...

[LIST]
[*]A /dev node such as /dev/mice can be made to appear simply by modprobing a kernel module. Whether there's a mouse plugged into your machine doesn't really matter ... Xorg can still see the device interface.
[*]Typically, the /dev nodes used by evdev are only created when you plug something into your machine, eg a USB mouse. So if you label one a core pointer (ie instruct X to fail to start if it's not there), and the /dev node doesn't exist, X will do exactly what it's told.
[/LIST]

You could try *not* making your evdev pointing device a core pointer, or maybe adding a redundant core input device to your xorg.conf that you know will always be there. The bottom line, I suppose, is that if you tell Xorg not to start without a specific device, it won't.

I hope that helps a little.

---

