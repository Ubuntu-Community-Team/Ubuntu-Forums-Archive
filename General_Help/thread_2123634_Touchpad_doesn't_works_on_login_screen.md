---
title: "Touchpad doesn't works on login screen"
date: 2013-03-08
forum: General Help
---

### Post by ubunet on 2013-03-08
The touchpad **ClickPad** doesn't work on login screen, **only after**. I need to click with a notebook left button to change user, typer password and start or press ENTER in keyboard.

---

### Post by ubunet on 2013-03-08
My Xorg log:
```
gustavo@NETUBU:/var/log$ egrep "synaptics|touchpad" Xorg.0.log
[    23.859] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    23.859] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    23.859] (II) LoadModule: "synaptics"
[    23.859] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    23.866] (II) Module synaptics: vendor="X.Org Foundation"
[    23.866] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    23.880] (II) synaptics: SynPS/2 Synaptics TouchPad: ignoring touch events for semi-multitouch device
[    23.880] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5772
[    23.880] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 5086
[    23.880] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    23.880] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    23.880] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    23.880] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    23.881] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    23.888] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    23.888] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    23.888] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.035
[    23.889] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    23.890] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"

```

---

### Post by ubunet on 2013-03-11
**Solved**. Changed the section below in file **/usr/share/X11/xorg.conf.d/50-synaptics.conf**

```

Section "InputClass"
        Identifier "touchpad catchall"
        Driver "synaptics"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
        Option "TapButton1" "1"
        Option "TapButton2" "3"
        Option "TapButton3" "2"
        Option "VertTwoFingerScroll" "1"
        Option "HorizTwoFingerScroll" "1"
EndSection
```

---

