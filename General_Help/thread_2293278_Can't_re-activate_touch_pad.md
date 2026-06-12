---
title: "Can't re-activate touch pad"
date: 2015-09-03
forum: General Help
---

### Post by Petro Dawg on 2015-09-03
My touchpad used to work but a few weeks ago I deactivated my touch pad using the GUI Mouse and Touchpad settings.  Lately I've been having issues with my logitech wireless mouse sometimes not responding at boot (it is working at the moment however) and I wanted to reactivate the touch pad... but there is no longer a place in the GUI to turn it back on.  Not sure what's happening with my pointing devices.

[ATTACH=CONFIG]264216[/ATTACH]

I tried the following in terminal without any luck...

```
~$ synclient TouchpadOff=0
Couldn't find synaptics properties. No synaptics driver loaded?

```

```
~$ gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled true

```

Pressing Fn+F7  (keyboard shortcut for touchpad on/off)

Output of xinput list...
```
~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech Unifying Device. Wireless PID:1028    id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; HD WebCam                                   id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; Acer WMI hotkeys                            id=12    [slave  keyboard (3)]
```

I noticed there is an error message during boot that might be related...
```
[   17.337613] usb 2-5: Device not responding to set address.
[   17.541604] usb 2-5: device not accepting address 4, error -71
[   17.653706] usb 2-5: new full-speed USB device number 5 using xhci_hcd
[   17.671008] usb 2-5: New USB device found, idVendor=04ca, idProduct=300b
[   17.671012] usb 2-5: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[   18.741845] init: failsafe main process (688) killed by TERM signal
```

Please let me what next course of action should be.  Thanks.

---

### Post by Petro Dawg on 2015-09-04
Bump.  Any ideas today?

---

