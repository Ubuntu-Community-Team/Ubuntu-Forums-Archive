---
title: "New Lenovo laptop, Ubuntu 14.04 LTS and touchpad problem"
date: 2015-06-10
forum: General Help
---

### Post by georgesgiralt on 2015-06-10
Hello !
My very old latop has to get retirement.... So I bought a Lenovo E540 (20C600JHFR) laptop which is fitted with a large touchpad. 
I was used to have the touchpad disabled when I typed on my previous laptop. So I would like to get the same behavior in this new one also. But it is not working. And this is annoying because the touchpad is very large so I always move the cursor when typing, which slows me down a lot. 
Some information :
1) the "disable when typing" is checked in the system/touchpad properties panel.
2) the X windows system says in /var/log/Xorg.0.log  : 
```

[    32.362] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event4)
[    32.362] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    32.362] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    32.362] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    32.362] (II) LoadModule: "synaptics"
[    32.362] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    32.362] (II) Module synaptics: vendor="X.Org Foundation"
[    32.362]    compiled for 1.15.0, module version = 1.7.4
[    32.362]    Module class: X.Org XInput Driver
[    32.362]    ABI class: X.Org XInput driver, version 20.0
[    32.362] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    32.362] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    32.362] (**) Option "Device" "/dev/input/event4"
[    32.380] (II) synaptics: SynPS/2 Synaptics TouchPad: found clickpad property
[    32.380] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1264 - 5675 (res 45)
[    32.380] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1171 - 4688 (res 52)
[    32.380] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    32.380] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    32.380] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left double triple
[    32.380] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    32.380] (**) Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
[    32.380] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    32.380] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    32.396] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input4/event4"
[    32.396] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 12)
[    32.396] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    32.396] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    32.396] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.035
[    32.396] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    32.396] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    32.396] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    32.396] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    32.396] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    32.396] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[    32.396] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    32.396] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/event5)
[    32.396] (**) TPPS/2 IBM TrackPoint: Applying InputClass "evdev pointer catchall"
[    32.396] (**) TPPS/2 IBM TrackPoint: Applying InputClass "trackpoint catchall"
[    32.396] (II) Using input driver 'evdev' for 'TPPS/2 IBM TrackPoint'
[    32.396] (**) TPPS/2 IBM TrackPoint: always reports core events
[    32.396] (**) evdev: TPPS/2 IBM TrackPoint: Device: "/dev/input/event5"
[    32.397] (--) evdev: TPPS/2 IBM TrackPoint: Vendor 0x2 Product 0xa
[    32.397] (--) evdev: TPPS/2 IBM TrackPoint: Found 3 mouse buttons
[    32.397] (--) evdev: TPPS/2 IBM TrackPoint: Found relative axes
[    32.397] (--) evdev: TPPS/2 IBM TrackPoint: Found x and y relative axes
[    32.397] (II) evdev: TPPS/2 IBM TrackPoint: Configuring as mouse
[    32.397] (**) Option "Emulate3Buttons" "true"
[    32.397] (**) Option "EmulateWheel" "true"
[    32.397] (**) Option "EmulateWheelButton" "2"
[    32.397] (**) Option "YAxisMapping" "4 5"
[    32.397] (**) evdev: TPPS/2 IBM TrackPoint: YAxisMapping: buttons 4 and 5
[    32.397] (**) Option "XAxisMapping" "6 7"
[    32.397] (**) evdev: TPPS/2 IBM TrackPoint: XAxisMapping: buttons 6 and 7
[    32.397] (**) evdev: TPPS/2 IBM TrackPoint: EmulateWheelButton: 2, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    32.397] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/serio2/input/input6/event5"
[    32.397] (II) XINPUT: Adding extended input device "TPPS/2 IBM TrackPoint" (type: MOUSE, id 13)
[    32.397] (II) evdev: TPPS/2 IBM TrackPoint: initialized for relative axes.
[    32.397] (**) TPPS/2 IBM TrackPoint: (accel) keeping acceleration scheme 1
[    32.397] (**) TPPS/2 IBM TrackPoint: (accel) acceleration profile 0
[    32.397] (**) TPPS/2 IBM TrackPoint: (accel) acceleration factor: 2.000
[    32.397] (**) TPPS/2 IBM TrackPoint: (accel) acceleration threshold: 4
[    32.397] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/mouse2)
[    32.397] (II) No input driver specified, ignoring this device.
[    32.397] (II) This device may have been added with another device file.

```

The xinput info is :
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Optical Mouse              	id=10	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=12	[slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                   	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=8	[slave  keyboard (3)]
    &#8627; Integrated Camera                       	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                  	id=14	[slave  keyboard (3)]

```

I would be delighted to have this behavior corrected as it is very annoying !
Many thanks in advance for your help.

---

