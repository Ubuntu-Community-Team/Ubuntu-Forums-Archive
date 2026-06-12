---
title: "Lubuntu 17.04 display errors"
date: 2017-10-09
forum: General Help
---

### Post by gabrieljim on 2017-10-09
Hey, everyone, I'm new here, I hope you can help me out.
I installed Lubuntu 17.04, I ran the Live CD and everything pretty much worked, but then when i installed it, the display looks like this.
[ATTACH=CONFIG]277056[/ATTACH]

As you can see, it's like the display is dragged left, theres that black space on the right.
[ATTACH=CONFIG]277057[/ATTACH]

This is how it looks with a regular screenshot, so it has to be a physical problem, I also have some problems with the grub, I already updated, could i get any help, please? COuld it be a bug of the 17.04?

---

### Post by Autodave on 2017-10-09
Your monitor should have a button (maybe a menu) where you can auto-center the screen. That should fix that problem.

---

### Post by ajgreeny on 2017-10-09
What cable are you using, VGA, HDMI, DVI?

That problem is often overcome with either HDMI or DVI, if you have that possibility, if not the display's own menu should help.
I found a couple of years ago, setting a slightly lower refresh rate might help a little bit, but probably not enough to get rid of that wide a black strip.

---

### Post by gabrieljim on 2017-10-09
Hey, sorry I took this long to respond, I had to study some stuff.

> **Autodave said:**
> Your monitor should have a button (maybe a menu) where you can auto-center the screen. That should fix that problem.

Yes, I didn't knew that, the thing is that I dual-boot with Windows, where evetyrhing looks good, so I guess i would have to be constantly moving it.

> **ajgreeny said:**
> What cable are you using, VGA, HDMI, DVI?

That problem is often overcome with either HDMI or DVI, if you have that possibility, if not the display's own menu should help.
I found a couple of years ago, setting a slightly lower refresh rate might help a little bit, but probably not enough to get rid of that wide a black strip.

Only VGA available, shamefully.


Another thing I didn't point out is that I can't change the resolution, in "monitor settings" there's only one to select.

---

### Post by gabrieljim on 2017-10-10
I'm gonna try and install 16.04 and see if it helps at all

---

### Post by gabrieljim on 2017-10-10
Changed to Xubuntu 14.04 and I have the same resolution problem, and the grub still looks bad and moves, I guess it's something with the monitor but I don't know what to do.

Someone help, please

---

### Post by Yellow Pasque on 2017-10-11
Post the contents of the /var/log/Xorg.0.log file. Use code tags as it's a lot of text.

---

### Post by gabrieljim on 2017-10-11
> **Temüjin said:**
> Post the contents of the /var/log/Xorg.0.log file. Use code tags as it's a lot of text.

Thanks for answering.
Here, I hope this helps at all.

Also, I downloaded grub-customizer and set the default resolution to 640x480, so now the resolution changed, but once again I can't change it, and the display is still kind of moved up and left like in the pic

```
[    30.844] 
X.Org X Server 1.18.3
Release Date: 2016-04-04
[    30.844] X Protocol Version 11, Revision 0
[    30.844] Build Operating System: Linux 3.13.0-86-generic i686 Ubuntu
[    30.844] Current Operating System: Linux Navi 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:06:14 UTC 2016 i686
[    30.844] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-31-generic root=UUID=3b7bc396-5c2a-48eb-bf56-d64fe5faad86 ro quiet splash vt.handoff=7
[    30.844] Build Date: 18 May 2016  01:07:07AM
[    30.844] xorg-server 2:1.18.3-1ubuntu2.2 (For technical support please see http://www.ubuntu.com/support) 
[    30.844] Current version of pixman: 0.33.6
[    30.844]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    30.844] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    30.844] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Oct 11 01:16:57 2017
[    30.857] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    30.857] (==) No Layout section.  Using the first Screen section.
[    30.857] (==) No screen section available. Using defaults.
[    30.857] (**) |-->Screen "Default Screen Section" (0)
[    30.857] (**) |   |-->Monitor "<default monitor>"
[    30.864] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    30.864] (==) Automatically adding devices
[    30.864] (==) Automatically enabling devices
[    30.864] (==) Automatically adding GPU devices
[    30.864] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    30.864] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    30.864]     Entry deleted from font path.
[    30.864] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    30.864]     Entry deleted from font path.
[    30.864] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    30.864]     Entry deleted from font path.
[    30.864] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    30.864]     Entry deleted from font path.
[    30.864] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    30.864]     Entry deleted from font path.
[    30.864] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    30.864] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    30.864] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    30.864] (II) Loader magic: 0x8031b700
[    30.864] (II) Module ABI versions:
[    30.864]     X.Org ANSI C Emulation: 0.4
[    30.864]     X.Org Video Driver: 20.0
[    30.865]     X.Org XInput driver : 22.1
[    30.865]     X.Org Server Extension : 9.0
[    30.866] (++) using VT number 7

[    30.866] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[    30.869] (--) PCI:*(0:1:0:0) 1106:3371:1849:3371 rev 1, Mem @ 0xc0000000/536870912, 0xfd000000/16777216, BIOS @ 0x????????/65536
[    30.877] (II) LoadModule: "glx"
[    30.893] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    31.060] (II) Module glx: vendor="X.Org Foundation"
[    31.060]     compiled for 1.18.3, module version = 1.0.0
[    31.060]     ABI class: X.Org Server Extension, version 9.0
[    31.061] (==) AIGLX enabled
[    31.061] (==) Matched openchrome as autoconfigured driver 0
[    31.061] (==) Matched modesetting as autoconfigured driver 1
[    31.061] (==) Matched fbdev as autoconfigured driver 2
[    31.061] (==) Matched vesa as autoconfigured driver 3
[    31.061] (==) Assigned the driver to the xf86ConfigLayout
[    31.061] (II) LoadModule: "openchrome"
[    31.061] (WW) Warning, couldn't open module openchrome
[    31.061] (II) UnloadModule: "openchrome"
[    31.061] (II) Unloading openchrome
[    31.061] (EE) Failed to load module "openchrome" (module does not exist, 0)
[    31.061] (II) LoadModule: "modesetting"
[    31.062] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    31.062] (II) Module modesetting: vendor="X.Org Foundation"
[    31.062]     compiled for 1.18.3, module version = 1.18.3
[    31.062]     Module class: X.Org Video Driver
[    31.062]     ABI class: X.Org Video Driver, version 20.0
[    31.062] (II) LoadModule: "fbdev"
[    31.062] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    31.062] (II) Module fbdev: vendor="X.Org Foundation"
[    31.062]     compiled for 1.18.1, module version = 0.4.4
[    31.062]     Module class: X.Org Video Driver
[    31.062]     ABI class: X.Org Video Driver, version 20.0
[    31.062] (II) LoadModule: "vesa"
[    31.063] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    31.063] (II) Module vesa: vendor="X.Org Foundation"
[    31.063]     compiled for 1.18.1, module version = 2.3.4
[    31.063]     Module class: X.Org Video Driver
[    31.063]     ABI class: X.Org Video Driver, version 20.0
[    31.063] (==) Matched openchrome as autoconfigured driver 0
[    31.063] (==) Matched modesetting as autoconfigured driver 1
[    31.063] (==) Matched fbdev as autoconfigured driver 2
[    31.063] (==) Matched vesa as autoconfigured driver 3
[    31.063] (==) Assigned the driver to the xf86ConfigLayout
[    31.063] (II) LoadModule: "openchrome"
[    31.063] (WW) Warning, couldn't open module openchrome
[    31.063] (II) UnloadModule: "openchrome"
[    31.063] (II) Unloading openchrome
[    31.063] (EE) Failed to load module "openchrome" (module does not exist, 0)
[    31.063] (II) LoadModule: "modesetting"
[    31.064] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    31.064] (II) Module modesetting: vendor="X.Org Foundation"
[    31.064]     compiled for 1.18.3, module version = 1.18.3
[    31.064]     Module class: X.Org Video Driver
[    31.064]     ABI class: X.Org Video Driver, version 20.0
[    31.064] (II) UnloadModule: "modesetting"
[    31.064] (II) Unloading modesetting
[    31.064] (II) Failed to load module "modesetting" (already loaded, 0)
[    31.064] (II) LoadModule: "fbdev"
[    31.064] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    31.064] (II) Module fbdev: vendor="X.Org Foundation"
[    31.064]     compiled for 1.18.1, module version = 0.4.4
[    31.064]     Module class: X.Org Video Driver
[    31.064]     ABI class: X.Org Video Driver, version 20.0
[    31.064] (II) UnloadModule: "fbdev"
[    31.064] (II) Unloading fbdev
[    31.064] (II) Failed to load module "fbdev" (already loaded, 0)
[    31.064] (II) LoadModule: "vesa"
[    31.064] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    31.064] (II) Module vesa: vendor="X.Org Foundation"
[    31.064]     compiled for 1.18.1, module version = 2.3.4
[    31.064]     Module class: X.Org Video Driver
[    31.064]     ABI class: X.Org Video Driver, version 20.0
[    31.064] (II) UnloadModule: "vesa"
[    31.064] (II) Unloading vesa
[    31.065] (II) Failed to load module "vesa" (already loaded, 0)
[    31.065] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    31.065] (II) FBDEV: driver for framebuffer: fbdev
[    31.065] (II) VESA: driver for VESA chipsets: vesa
[    31.065] (EE) open /dev/dri/card0: No such file or directory
[    31.065] (EE) open /dev/dri/card0: No such file or directory
[    31.065] (WW) Falling back to old probe method for modesetting
[    31.065] (EE) open /dev/dri/card0: No such file or directory
[    31.065] (EE) open /dev/dri/card0: No such file or directory
[    31.065] (II) Loading sub module "fbdevhw"
[    31.065] (II) LoadModule: "fbdevhw"
[    31.065] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    31.065] (II) Module fbdevhw: vendor="X.Org Foundation"
[    31.065]     compiled for 1.18.3, module version = 0.0.2
[    31.065]     ABI class: X.Org Video Driver, version 20.0
[    31.065] (**) FBDEV(2): claimed PCI slot 1@0:0:0
[    31.065] (II) FBDEV(2): using default device
[    31.066] (WW) Falling back to old probe method for vesa
[    31.066] (EE) Screen 0 deleted because of no matching config section.
[    31.066] (II) UnloadModule: "modesetting"
[    31.066] (EE) Screen 0 deleted because of no matching config section.
[    31.066] (II) UnloadModule: "modesetting"
[    31.066] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    31.066] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    31.066] (==) FBDEV(0): RGB weight 888
[    31.066] (==) FBDEV(0): Default visual is TrueColor
[    31.066] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    31.066] (II) FBDEV(0): hardware: VESA VGA (video memory: 1216kB)
[    31.066] (II) FBDEV(0): checking modes against framebuffer device...
[    31.066] (II) FBDEV(0): checking modes against monitor...
[    31.066] (--) FBDEV(0): Virtual size is 640x480 (pitch 640)
[    31.066] (**) FBDEV(0):  Built-in mode "current": 30.7 MHz, 36.9 kHz, 73.3 Hz
[    31.066] (II) FBDEV(0): Modeline "current"x0.0   30.72  640 672 752 832  480 484 488 504 -hsync -vsync -csync (36.9 kHz b)
[    31.066] (==) FBDEV(0): DPI set to (96, 96)
[    31.066] (II) Loading sub module "fb"
[    31.066] (II) LoadModule: "fb"
[    31.066] (II) Loading /usr/lib/xorg/modules/libfb.so
[    31.076] (II) Module fb: vendor="X.Org Foundation"
[    31.076]     compiled for 1.18.3, module version = 1.0.0
[    31.076]     ABI class: X.Org ANSI C Emulation, version 0.4
[    31.076] (**) FBDEV(0): using shadow framebuffer
[    31.076] (II) Loading sub module "shadow"
[    31.076] (II) LoadModule: "shadow"
[    31.077] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    31.077] (II) Module shadow: vendor="X.Org Foundation"
[    31.077]     compiled for 1.18.3, module version = 1.1.0
[    31.077]     ABI class: X.Org ANSI C Emulation, version 0.4
[    31.077] (II) UnloadModule: "vesa"
[    31.077] (II) Unloading vesa
[    31.077] (==) Depth 24 pixmap format is 32 bpp
[    31.077] (II) FBDEV(0): FBIOBLANK: Invalid argument (Screen blanking not supported by kernel - disabling)
[    31.095] (==) FBDEV(0): Backing store enabled
[    31.101] (==) FBDEV(0): DPMS enabled
[    31.102] (==) RandR enabled
[    31.118] (II) SELinux: Disabled on system
[    31.120] (II) AIGLX: Screen 0 is not DRI2 capable
[    31.120] (EE) AIGLX: reverting to software rendering
[    31.715] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    31.717] (II) AIGLX: Loaded and initialized swrast
[    31.717] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    31.908] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    31.908] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    31.909] (II) LoadModule: "evdev"
[    31.909] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    31.928] (II) Module evdev: vendor="X.Org Foundation"
[    31.928]     compiled for 1.18.1, module version = 2.10.1
[    31.928]     Module class: X.Org XInput Driver
[    31.928]     ABI class: X.Org XInput driver, version 22.1
[    31.928] (II) Using input driver 'evdev' for 'Power Button'
[    31.928] (**) Power Button: always reports core events
[    31.928] (**) evdev: Power Button: Device: "/dev/input/event1"
[    31.928] (--) evdev: Power Button: Vendor 0 Product 0x1
[    31.928] (--) evdev: Power Button: Found keys
[    31.928] (II) evdev: Power Button: Configuring as keyboard
[    31.928] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    31.929] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    31.929] (**) Option "xkb_rules" "evdev"
[    31.929] (**) Option "xkb_model" "pc105"
[    31.929] (**) Option "xkb_layout" "latam"
[    31.965] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    31.965] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    31.965] (II) Using input driver 'evdev' for 'Power Button'
[    31.965] (**) Power Button: always reports core events
[    31.965] (**) evdev: Power Button: Device: "/dev/input/event0"
[    31.965] (--) evdev: Power Button: Vendor 0 Product 0x1
[    31.965] (--) evdev: Power Button: Found keys
[    31.965] (II) evdev: Power Button: Configuring as keyboard
[    31.965] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    31.965] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    31.965] (**) Option "xkb_rules" "evdev"
[    31.965] (**) Option "xkb_model" "pc105"
[    31.965] (**) Option "xkb_layout" "latam"
[    31.966] (II) config/udev: Adding input device HDA VIA VT82xx Line Out Side (/dev/input/event9)
[    31.966] (II) No input driver specified, ignoring this device.
[    31.966] (II) This device may have been added with another device file.
[    31.967] (II) config/udev: Adding input device HDA VIA VT82xx Mic (/dev/input/event4)
[    31.967] (II) No input driver specified, ignoring this device.
[    31.967] (II) This device may have been added with another device file.
[    31.968] (II) config/udev: Adding input device HDA VIA VT82xx Line (/dev/input/event5)
[    31.968] (II) No input driver specified, ignoring this device.
[    31.968] (II) This device may have been added with another device file.
[    31.968] (II) config/udev: Adding input device HDA VIA VT82xx Line Out Front (/dev/input/event6)
[    31.968] (II) No input driver specified, ignoring this device.
[    31.968] (II) This device may have been added with another device file.
[    31.969] (II) config/udev: Adding input device HDA VIA VT82xx Line Out Surround (/dev/input/event7)
[    31.969] (II) No input driver specified, ignoring this device.
[    31.969] (II) This device may have been added with another device file.
[    31.970] (II) config/udev: Adding input device HDA VIA VT82xx Line Out CLFE (/dev/input/event8)
[    31.970] (II) No input driver specified, ignoring this device.
[    31.970] (II) This device may have been added with another device file.
[    31.971] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    31.971] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    31.971] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    31.971] (**) AT Translated Set 2 keyboard: always reports core events
[    31.971] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    31.971] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    31.971] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    31.971] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    31.971] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    31.971] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 8)
[    31.971] (**) Option "xkb_rules" "evdev"
[    31.971] (**) Option "xkb_model" "pc105"
[    31.971] (**) Option "xkb_layout" "latam"
[    31.972] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event3)
[    31.972] (**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
[    31.972] (II) Using input driver 'evdev' for 'ImPS/2 Generic Wheel Mouse'
[    31.972] (**) ImPS/2 Generic Wheel Mouse: always reports core events
[    31.972] (**) evdev: ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event3"
[    31.972] (--) evdev: ImPS/2 Generic Wheel Mouse: Vendor 0x2 Product 0x5
[    31.973] (--) evdev: ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
[    31.973] (--) evdev: ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
[    31.973] (--) evdev: ImPS/2 Generic Wheel Mouse: Found relative axes
[    31.973] (--) evdev: ImPS/2 Generic Wheel Mouse: Found x and y relative axes
[    31.973] (II) evdev: ImPS/2 Generic Wheel Mouse: Configuring as mouse
[    31.973] (II) evdev: ImPS/2 Generic Wheel Mouse: Adding scrollwheel support
[    31.973] (**) evdev: ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
[    31.973] (**) evdev: ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    31.973] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input4/event3"
[    31.973] (II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE, id 9)
[    31.973] (II) evdev: ImPS/2 Generic Wheel Mouse: initialized for relative axes.
[    31.973] (**) ImPS/2 Generic Wheel Mouse: (accel) keeping acceleration scheme 1
[    31.973] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration profile 0
[    31.973] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration factor: 2.000
[    31.973] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration threshold: 4
[    31.974] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse0)
[    31.974] (II) No input driver specified, ignoring this device.
[    31.974] (II) This device may have been added with another device file.


```

---

### Post by Yellow Pasque on 2017-10-11
```
(--) PCI:*(0:1:0:0) 1106:3371:1849:3371 rev 1
```
Looks like a VIA P4M900, Chrome9 graphics. That's bad news.
Quite frankly, your best bet is to buy a cheap, used video card, especially if you want to watch video.

If you're willing to spend a few dollars, then give us more information on your system. Hopefully, it has a PCI-E slot.

If you want to continue to troubleshoot this problem, I would try to add 'xforcevesa' to the boot parameters.
```
(--) PCI:*(0:1:0:0) 1106:3371:1849:3371 rev 1,
```

---

### Post by gabrieljim on 2017-10-11
> **Temüjin said:**
> ```
(--) PCI:*(0:1:0:0) 1106:3371:1849:3371 rev 1
```
Looks like a VIA P4M900, Chrome9 graphics. That's bad news.
Quite frankly, your best bet is to buy a cheap, used video card, especially if you want to watch video.

If you're willing to spend a few dollars, then give us more information on your system. Hopefully, it has a PCI-E slot.

If you want to continue to troubleshoot this problem, I would try to add 'xforcevesa' to the boot parameters.
```
(--) PCI:*(0:1:0:0) 1106:3371:1849:3371 rev 1,
```

Unfortunately, it's out of consideration to buy anything, third world and stuff.
So weird though, why did it work on the "Try Ubuntu" but when installed everything gets messed up?
I'll try to add the thing you said, what file am I looking for?

---

### Post by gabrieljim on 2017-10-12
So, pretty dumb, I just clicked the "auto adjust" button on the monitor itself, so that fixed the screen being shifted and all.
But I can't change my screen's resolution, and xrandr gives this:

xrandr: Failed to get size of gamma for output default

---

### Post by Yellow Pasque on 2017-10-12
Try making an /etc/X11/xorg.conf file:
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

---

### Post by gabrieljim on 2017-10-12
> **Temüjin said:**
> Try making an /etc/X11/xorg.conf file:
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

Awesome! That worked!
When I type "xrandr" into the terminal I still get the same error, but now I can change the resolution.
Thank you man.

---

### Post by Yellow Pasque on 2017-10-12
> **gabrieljim said:**
> Thank you man.

Yeah, I try to help out the people in the third world and stuff.

---

