---
title: "Black Screen on Startup"
date: 2017-03-23
forum: General Help
---

### Post by mk2209 on 2017-03-23
Hello,

I I have an old Laptop Compaq Armada E500 where I installed Lubuntu 16.10. After install the System did boot up correctly. Then I installed all the Software-Updates and since then on bootup,  I have a black Screen It appears after the Lubuntu Logo with the five blue dots and before the mouse curser should show up.

If I go into the advanced menu of grub,  I can choose "Ubuntu with Linux 4.0.8-41" and "Ubuntu with Linux 4.0.8-22". If I choose 4.0.8.22 the System boots up correctly. If I choose 4.0.8-22  I have the black Screen.

Is It possible to configure the System to always boot 4.0.8-22 instead of 4.0.8-41? What is the difference  between the two versions?

Can someone help me, thanks.

---

### Post by Bashing-om on 2017-03-23
mk2209; Hello; Welcome to the forum .

> 
Is It possible to configure the System to always boot 4.0.8-22 instead of 4.0.8-41?

Short answer, Yes . Do you rally need to ? Let us see, as the better thing is to find the cause of the issues with the -41 kernel. Any number of things can change between versions - security updates, bug fixes, and hardware integration for just a few things .

Let us at this time suppose that the graphic's driver is broke for the -41 kernel. See about installing a driver .
To that end post back - Between Code Tags - the output of terminal commands:
Here does not matter which kernel you boot . we get back to the -41 version later.
```

lspci -vnn | grep -i VGA
sudo lshw -C display

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by mk2209 on 2017-03-23
Hello Bashing-om,

lspci outputs:
```

01:00.0 VGA compatible Controller [0300}: Advanced Micro Devices, Inc. [AMD/ATI] Rage Mobility AGP 2x Series [1002:4c4d] (rev 64) (prog-if 00 [VGA Controller]) 
```



and with sudo lshw I get an error message :
```

Memory Access error (core Image written)
```
I have german language installed and I get german messages, so  I don't know exactly, if this is the right translation for this message. But I think, correspondingly it should.

---

### Post by Bashing-om on 2017-03-23
mk2209; Well, Not !

I would have expected the result of ' sudo lshw -C display' to be something like:
> 
sysop@x1604:~$ sudo lshw -C display
[sudo] password for sysop: 
  *-display               
       description: VGA compatible controller
       product: GK208 [GeForce GT 710B]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:29 memory:fb000000-fbffffff memory:d8000000-dfffffff memory:e6000000-e7ffffff ioport:4c00(size=128) memory:fc000000-fc07ffff
sysop@x1604:~$ 

where I am running a nVidia card. I presently do not know what to make of " Memory Access error " when you execute the command !

Do we get any hints from the log file ?
post back :
```

cat /var/log/Xorg.0.log

```

In research on your card I find:
> 
Proprietary ATI driver
This chip is not supported by the proprietary ATI driver.

So our only option here appears to be the mach64 driver.

But, we shall see -
[INDENT][INDENT][INDENT]what we can see[/INDENT][/INDENT][/INDENT]

---

### Post by mk2209 on 2017-03-24
Hello,

here is the logfile:

```
[    45.178] 

X.Org X Server 1.18.4

Release Date: 2016-07-19

[    45.178] X Protocol Version 11, Revision 0

[    45.179] Build Operating System: Linux 4.4.0-45-generic i686 Ubuntu

[    45.179] Current Operating System: Linux mk2209-Armada-E500 4.8.0-22-generic #24-Ubuntu SMP Sat Oct 8 09:14:42 UTC 2016 i686

[    45.179] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.8.0-22-generic root=UUID=08e5bcc2-573c-41f3-bfe8-df9c42074e1a ro quiet splash vt.handoff=7

[    45.179] Build Date: 02 November 2016  10:05:40PM

[    45.179] xorg-server 2:1.18.4-1ubuntu6.1 (For technical support please see http://www.ubuntu.com/support) 

[    45.179] Current version of pixman: 0.33.6

[    45.179]     Before reporting problems, check http://wiki.x.org

    to make sure that you have the latest version.

[    45.179] Markers: (--) probed, (**) from config file, (==) default setting,

    (++) from command line, (!!) notice, (II) informational,

    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.

[    45.181] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Mar 24 20:13:35 2017

[    45.197] (==) Using system config directory "/usr/share/X11/xorg.conf.d"

[    45.199] (==) No Layout section.  Using the first Screen section.

[    45.199] (==) No screen section available. Using defaults.

[    45.201] (**) |-->Screen "Default Screen Section" (0)

[    45.201] (**) |   |-->Monitor "<default monitor>"

[    45.226] (==) No monitor specified for screen "Default Screen Section".

    Using a default monitor configuration.

[    45.226] (==) Automatically adding devices

[    45.226] (==) Automatically enabling devices

[    45.226] (==) Automatically adding GPU devices

[    45.227] (==) Max clients allowed: 256, resource mask: 0x1fffff

[    45.227] (WW) The directory "/usr/share/fonts/X11/misc" does not exist.

[    45.227]     Entry deleted from font path.

[    45.227] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.

[    45.227]     Entry deleted from font path.

[    45.227] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.

[    45.227]     Entry deleted from font path.

[    45.227] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.

[    45.227]     Entry deleted from font path.

[    45.227] (WW) The directory "/usr/share/fonts/X11/Type1" does not exist.

[    45.227]     Entry deleted from font path.

[    45.227] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.

[    45.227]     Entry deleted from font path.

[    45.227] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.

[    45.227]     Entry deleted from font path.

[    45.231] (==) FontPath set to:

    built-ins

[    45.231] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"

[    45.231] (II) The server relies on udev to provide the list of input devices.

    If no devices become available, reconfigure udev or disable AutoAddDevices.

[    45.259] (II) Loader magic: 0x8029b700

[    45.259] (II) Module ABI versions:

[    45.259]     X.Org ANSI C Emulation: 0.4

[    45.259]     X.Org Video Driver: 20.0

[    45.259]     X.Org XInput driver : 22.1

[    45.259]     X.Org Server Extension : 9.0

[    45.276] (++) using VT number 7

&#12288;

[    45.277] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration

[    45.292] (--) PCI:*(0:1:0:0) 1002:4c4d:0e11:b160 rev 100, Mem @ 0x40000000/16777216, 0x41000000/4096, I/O @ 0x00002000/256, BIOS @ 0x????????/131072

[    45.293] (II) LoadModule: "glx"

[    45.355] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so

[    45.793] (II) Module glx: vendor="X.Org Foundation"

[    45.793]     compiled for 1.18.4, module version = 1.0.0

[    45.794]     ABI class: X.Org Server Extension, version 9.0

[    45.794] (==) AIGLX enabled

[    45.794] (==) Matched ati as autoconfigured driver 0

[    45.794] (==) Matched modesetting as autoconfigured driver 1

[    45.794] (==) Matched fbdev as autoconfigured driver 2

[    45.794] (==) Matched vesa as autoconfigured driver 3

[    45.794] (==) Assigned the driver to the xf86ConfigLayout

[    45.794] (II) LoadModule: "ati"

[    45.795] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so

[    45.796] (II) Module ati: vendor="X.Org Foundation"

[    45.796]     compiled for 1.18.4, module version = 7.7.1

[    45.796]     Module class: X.Org Video Driver

[    45.796]     ABI class: X.Org Video Driver, version 20.0

[    45.796] (II) LoadModule: "mach64"

[    45.798] (WW) Warning, couldn't open module mach64

[    45.798] (II) UnloadModule: "mach64"

[    45.798] (II) Unloading mach64

[    45.798] (EE) Failed to load module "mach64" (module does not exist, 0)

[    45.798] (II) LoadModule: "modesetting"

[    45.799] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so

[    45.799] (II) Module modesetting: vendor="X.Org Foundation"

[    45.799]     compiled for 1.18.4, module version = 1.18.4

[    45.800]     Module class: X.Org Video Driver

[    45.800]     ABI class: X.Org Video Driver, version 20.0

[    45.800] (II) LoadModule: "fbdev"

[    45.801] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so

[    45.801] (II) Module fbdev: vendor="X.Org Foundation"

[    45.801]     compiled for 1.18.1, module version = 0.4.4

[    45.801]     Module class: X.Org Video Driver

[    45.801]     ABI class: X.Org Video Driver, version 20.0

[    45.802] (II) LoadModule: "vesa"

[    45.802] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so

[    45.807] (II) Module vesa: vendor="X.Org Foundation"

[    45.807]     compiled for 1.18.1, module version = 2.3.4

[    45.807]     Module class: X.Org Video Driver

[    45.808]     ABI class: X.Org Video Driver, version 20.0

[    45.808] (II) modesetting: Driver for Modesetting Kernel Drivers: kms

[    45.808] (II) FBDEV: driver for framebuffer: fbdev

[    45.808] (II) VESA: driver for VESA chipsets: vesa

[    45.809] (EE) open /dev/dri/card0: No such file or directory

[    45.809] (WW) Falling back to old probe method for modesetting

[    45.809] (EE) open /dev/dri/card0: No such file or directory

[    45.809] (II) Loading sub module "fbdevhw"

[    45.809] (II) LoadModule: "fbdevhw"

[    45.810] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so

[    45.811] (II) Module fbdevhw: vendor="X.Org Foundation"

[    45.811]     compiled for 1.18.4, module version = 0.0.2

[    45.811]     ABI class: X.Org Video Driver, version 20.0

[    45.811] (**) FBDEV(1): claimed PCI slot 1@0:0:0

[    45.811] (II) FBDEV(1): using default device

[    45.811] (WW) Falling back to old probe method for vesa

[    45.811] (EE) Screen 0 deleted because of no matching config section.

[    45.811] (II) UnloadModule: "modesetting"

[    45.812] (II) FBDEV(0): Creating default Display subsection in Screen section

    "Default Screen Section" for depth/fbbpp 24/24

[    45.812] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 24

[    45.812] (==) FBDEV(0): RGB weight 888

[    45.812] (==) FBDEV(0): Default visual is TrueColor

[    45.812] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)

[    45.812] (II) FBDEV(0): hardware: VESA VGA (video memory: 2304kB)

[    45.812] (II) FBDEV(0): checking modes against framebuffer device...

[    45.812] (II) FBDEV(0): checking modes against monitor...

[    45.838] (--) FBDEV(0): Virtual size is 1024x768 (pitch 1024)

[    45.838] (**) FBDEV(0):  Built-in mode "current": 78.7 MHz, 59.9 kHz, 75.7 Hz

[    45.838] (II) FBDEV(0): Modeline "current"x0.0   78.65  1024 1056 1184 1312  768 772 776 792 -hsync -vsync -csync (59.9 kHz b)

[    45.838] (==) FBDEV(0): DPI set to (96, 96)

[    45.839] (II) Loading sub module "fb"

[    45.839] (II) LoadModule: "fb"

[    45.840] (II) Loading /usr/lib/xorg/modules/libfb.so

[    45.844] (II) Module fb: vendor="X.Org Foundation"

[    45.844]     compiled for 1.18.4, module version = 1.0.0

[    45.844]     ABI class: X.Org ANSI C Emulation, version 0.4

[    45.844] (**) FBDEV(0): using shadow framebuffer

[    45.844] (II) Loading sub module "shadow"

[    45.844] (II) LoadModule: "shadow"

[    45.845] (II) Loading /usr/lib/xorg/modules/libshadow.so

[    45.846] (II) Module shadow: vendor="X.Org Foundation"

[    45.846]     compiled for 1.18.4, module version = 1.1.0

[    45.846]     ABI class: X.Org ANSI C Emulation, version 0.4

[    45.846] (II) UnloadModule: "vesa"

[    45.846] (II) Unloading vesa

[    45.847] (==) Depth 24 pixmap format is 32 bpp

[    45.847] (II) FBDEV(0): FBIOBLANK: Invalid argument (Screen blanking not supported by kernel - disabling)

[    45.882] (==) FBDEV(0): Backing store enabled

[    45.889] (==) FBDEV(0): DPMS enabled

[    45.890] (==) RandR enabled

[    45.995] (II) SELinux: Disabled on system

[    46.001] (II) AIGLX: Screen 0 is not DRI2 capable

[    46.002] (EE) AIGLX: reverting to software rendering

[    47.101] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer

[    47.124] (II) AIGLX: Loaded and initialized swrast

[    47.124] (II) GLX: Initialized DRISWRAST GL provider for screen 0

[    47.588] (II) config/udev: Adding input device Power Button (/dev/input/event2)

[    47.588] (**) Power Button: Applying InputClass "evdev keyboard catchall"

[    47.588] (II) LoadModule: "evdev"

[    47.589] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so

[    47.620] (II) Module evdev: vendor="X.Org Foundation"

[    47.620]     compiled for 1.18.3, module version = 2.10.2

[    47.620]     Module class: X.Org XInput Driver

[    47.620]     ABI class: X.Org XInput driver, version 22.1

[    47.621] (II) Using input driver 'evdev' for 'Power Button'

[    47.621] (**) Power Button: always reports core events

[    47.621] (**) evdev: Power Button: Device: "/dev/input/event2"

[    47.621] (--) evdev: Power Button: Vendor 0 Product 0x1

[    47.621] (--) evdev: Power Button: Found keys

[    47.621] (II) evdev: Power Button: Configuring as keyboard

[    47.622] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"

[    47.622] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)

[    47.622] (**) Option "xkb_rules" "evdev"

[    47.622] (**) Option "xkb_model" "pc105"

[    47.622] (**) Option "xkb_layout" "de"

[    47.766] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)

[    47.766] (II) No input driver specified, ignoring this device.

[    47.766] (II) This device may have been added with another device file.

[    47.769] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)

[    47.769] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"

[    47.769] (II) Using input driver 'evdev' for 'Sleep Button'

[    47.769] (**) Sleep Button: always reports core events

[    47.769] (**) evdev: Sleep Button: Device: "/dev/input/event0"

[    47.770] (--) evdev: Sleep Button: Vendor 0 Product 0x3

[    47.770] (--) evdev: Sleep Button: Found keys

[    47.770] (II) evdev: Sleep Button: Configuring as keyboard

[    47.770] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0/event0"

[    47.770] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 7)

[    47.770] (**) Option "xkb_rules" "evdev"

[    47.770] (**) Option "xkb_model" "pc105"

[    47.770] (**) Option "xkb_layout" "de"

[    47.774] (II) config/udev: Adding input device ES1978 (/dev/input/event5)

[    47.775] (**) ES1978: Applying InputClass "evdev keyboard catchall"

[    47.775] (II) Using input driver 'evdev' for 'ES1978'

[    47.775] (**) ES1978: always reports core events

[    47.775] (**) evdev: ES1978: Device: "/dev/input/event5"

[    47.775] (--) evdev: ES1978: Vendor 0x125d Product 0x1978

[    47.775] (--) evdev: ES1978: Found keys

[    47.775] (II) evdev: ES1978: Configuring as keyboard

[    47.775] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:08.0/input/input12/event5"

[    47.776] (II) XINPUT: Adding extended input device "ES1978" (type: KEYBOARD, id 8)

[    47.776] (**) Option "xkb_rules" "evdev"

[    47.776] (**) Option "xkb_model" "pc105"

[    47.776] (**) Option "xkb_layout" "de"

[    47.781] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)

[    47.781] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"

[    47.781] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'

[    47.781] (**) AT Translated Set 2 keyboard: always reports core events

[    47.781] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"

[    47.782] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1

[    47.782] (--) evdev: AT Translated Set 2 keyboard: Found keys

[    47.782] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard

[    47.782] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"

[    47.782] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)

[    47.782] (**) Option "xkb_rules" "evdev"

[    47.782] (**) Option "xkb_model" "pc105"

[    47.782] (**) Option "xkb_layout" "de"

[    47.787] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event4)

[    47.787] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"

[    47.787] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"

[    47.787] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"

[    47.787] (II) LoadModule: "synaptics"

[    47.788] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so

[    47.789] (II) Module synaptics: vendor="X.Org Foundation"

[    47.789]     compiled for 1.18.3, module version = 1.8.3

[    47.790]     Module class: X.Org XInput Driver

[    47.790]     ABI class: X.Org XInput driver, version 22.1

[    47.790] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'

[    47.790] (**) SynPS/2 Synaptics TouchPad: always reports core events

[    47.790] (**) Option "Device" "/dev/input/event4"

[    47.791] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472 (res 85)

[    47.791] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448 (res 94)

[    47.791] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255

[    47.791] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15

[    47.791] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple

[    47.791] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7

[    47.791] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found

[    47.791] (**) SynPS/2 Synaptics TouchPad: always reports core events

[    47.792] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input11/event4"

[    47.792] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 10)

[    47.803] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5

[    47.803] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75

[    47.803] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.040

[    47.804] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1

[    47.804] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1

[    47.804] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000

[    47.804] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4

[    47.805] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found

[    47.807] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)

[    47.807] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"

[  1013.223] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found

&#12288;

```


The logfile reports that the mach64-module could not be loaded as it does not exist.  So the next step would be to install mach64?

---

### Post by Bashing-om on 2017-03-24
mk2209; Well well ...

We have a known bug:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati-lts-xenial/+bug/1611982](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati-lts-xenial/+bug/1611982)

Let's see what we can do .

What now is installed for X's driver(s)
```

hwe-support-status --verbose ##may not apply ??
dpkg -l | grep linux-
dpkg -l  xserver-xorg-video-r128-lts-xenial xserver-xorg-video-mach64-lts-xenial

```
Be aware :
> 
This bug was fixed in the package xserver-xorg-video-ati-lts-xenial - 1:7.7.0-1~trusty2


[INDENT][INDENT]maybe Yes
[INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mk2209 on 2017-03-25
Hello,

with Hwe I get:
```
ii  linux-base                                 4.0ubuntu1                               all          Linux image base package
ii  linux-firmware                             1.161.1                                  all          Firmware for Linux kernel drivers
ii  linux-generic                              4.8.0.41.52                              i386         Complete Generic Linux kernel and headers
ii  linux-headers-4.8.0-22                     4.8.0-22.24                              all          Header files related to Linux kernel version 4.8.0
ii  linux-headers-4.8.0-22-generic             4.8.0-22.24                              i386         Linux kernel headers for version 4.8.0 on 32 bit x86 SMP
ii  linux-headers-4.8.0-41                     4.8.0-41.44                              all          Header files related to Linux kernel version 4.8.0
ii  linux-headers-4.8.0-41-generic             4.8.0-41.44                              i386         Linux kernel headers for version 4.8.0 on 32 bit x86 SMP
ii  linux-headers-generic                      4.8.0.41.52                              i386         Generic Linux kernel headers
ii  linux-image-4.8.0-22-generic               4.8.0-22.24                              i386         Linux kernel image for version 4.8.0 on 32 bit x86 SMP
ii  linux-image-4.8.0-41-generic               4.8.0-41.44                              i386         Linux kernel image for version 4.8.0 on 32 bit x86 SMP
ii  linux-image-extra-4.8.0-22-generic         4.8.0-22.24                              i386         Linux kernel extra modules for version 4.8.0 on 32 bit x86 SMP
ii  linux-image-extra-4.8.0-41-generic         4.8.0-41.44                              i386         Linux kernel extra modules for version 4.8.0 on 32 bit x86 SMP
ii  linux-image-generic                        4.8.0.41.52                              i386         Generic Linux kernel image
ii  syslinux-common                            3:6.03+dfsg-14                           all          collection of bootloaders (common)
ii  syslinux-legacy                            2:3.63+dfsg-2ubuntu8                     i386         Bootloader for Linux/i386 using MS-DOS floppies
```


dpkg -l | grep Linux- says:
```
Only LTS releases have Hardware Enablement stacks
```


And "dpkg -l  xserver-xorg-video-r128..." says that no package can be found or similar.

I searched manually for this package and I have downloaded  the file [http://launchpadlibrarian.net/278423308/xserver-xorg-video-radeon-lts-xenial_7.7.0-1~trusty2_i386.deb](http://launchpadlibrarian.net/278423308/xserver-xorg-video-radeon-lts-xenial_7.7.0-1~trusty2_i386.deb) and tried to install it. But I don't know if it is installed now. I double clicked the file and clicked on "install". It said "installing", but when it is ready I get no confirmation saying that it is installed. I only have the option to click on "install" again.

I did already reboot, but the black screen is still there.

---

### Post by Bashing-om on 2017-03-25
mk2209; Hummm ..

Well, we know we have to install a driver ; question is what else do we need to install to support the driver ?
What modules ( a driver is a module in linux ) are installed:
show:
```

lsmod
dpkg -l | grep "xserver-xorg-video*"

```

AND --
does a depreciated config file exist ?
show me:
```

ls -al /etc/X11/xorg.conf

```


Support for the driver: are these installed ?
```

dpkg -l xserver-xorg-core libgl1-mesa-glx libgl1-mesa-dri libgl1-mesa-glx:i386 libgl1-mesa-dri:i386 

```

My target here is " xserver-xorg-video-mach64" ( our needed DDX driver ).

[INDENT][INDENT]look'n to see
[INDENT][INDENT][INDENT]what we can do
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mk2209 on 2017-03-25
Hello,


lsmod:
```
Module                  Size  Used by
ccm                    20480  2
rtl8xxxu              110592  0
arc4                   16384  2
rtl8192cu              65536  0
rtl_usb                20480  1 rtl8192cu
rtl8192c_common        49152  1 rtl8192cu
rtlwifi                69632  3 rtl_usb,rtl8192c_common,rtl8192cu
mac80211              679936  4 rtl_usb,rtlwifi,rtl8192cu,rtl8xxxu
cfg80211              512000  2 mac80211,rtlwifi
snd_es1968             28672  2
snd_mpu401_uart        16384  1 snd_es1968
snd_ac97_codec        106496  1 snd_es1968
tea575x                16384  1 snd_es1968
gameport               16384  1 snd_es1968
videodev              159744  2 tea575x,snd_es1968
media                  36864  1 videodev
snd_rawmidi            28672  1 snd_mpu401_uart
snd_seq_device         16384  1 snd_rawmidi
ac97_bus               16384  1 snd_ac97_codec
snd_pcm                94208  2 snd_ac97_codec,snd_es1968
snd_timer              32768  1 snd_pcm
snd                    69632  11 snd_ac97_codec,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_es1968,snd_pcm
input_leds             16384  0
joydev                 20480  0
soundcore              16384  1 snd
serio_raw              16384  0
pcmcia                 57344  0
smsc_ircc2             32768  0
shpchp                 32768  0
yenta_socket           40960  0
irda                  180224  1 smsc_ircc2
i2c_piix4              20480  0
pcmcia_rsrc            20480  1 yenta_socket
pcmcia_core            24576  3 yenta_socket,pcmcia,pcmcia_rsrc
mac_hid                16384  0
parport_pc             32768  1
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              20480  0
x_tables               24576  1 ip_tables
autofs4                40960  2
psmouse               122880  0
e100                   36864  0
mii                    16384  1 e100
pata_acpi              16384  0
floppy                 61440  0
fjes                   28672  0

```


dpkg -l | grep "xserver-xorg-video*":
```
Eii  xserver-xorg-video-all                     1:7.7+13ubuntu4                          i386         X.Org X server -- output driver metapackage
ii  xserver-xorg-video-amdgpu                  1.1.2-1                                  i386         X.Org X server -- AMDGPU display driver
ii  xserver-xorg-video-ati                     1:7.7.1-1                                i386         X.Org X server -- AMD/ATI display driver wrapper
ii  xserver-xorg-video-fbdev                   1:0.4.4-1build5                          i386         X.Org X server -- fbdev display driver
ii  xserver-xorg-video-intel                   2:2.99.917+git20160706-1ubuntu1          i386         X.Org X server -- Intel i8xx, i9xx display driver
ii  xserver-xorg-video-nouveau                 1:1.0.12-2                               i386         X.Org X server -- Nouveau display driver
ii  xserver-xorg-video-radeon                  1:7.7.1-1                                i386         X.Org X server -- AMD/ATI Radeon display driver
ii  xserver-xorg-video-vesa                    1:2.3.4-1build2                          i386         X.Org X server -- VESA display driver
ii  xserver-xorg-video-vmware                  1:13.1.0-2ubuntu3                        i386         X.Org X server -- VMware display driver
```



xorg.conf does not exist



dpkg -l xserver-xorg-core... :
```
||/ Name                      Version           Architektur       Beschreibung
+++-=========================-=================-=================-=======================================================
ii  libgl1-mesa-dri:i386      12.0.6-0ubuntu0.1 i386              free implementation of the OpenGL API -- DRI modules
ii  libgl1-mesa-glx:i386      12.0.6-0ubuntu0.1 i386              free implementation of the OpenGL API -- GLX runtime
ii  xserver-xorg-core         2:1.18.4-1ubuntu6 i386              Xorg X server - core Server

```

---

### Post by Bashing-om on 2017-03-25
mk2209; Hey ...

```

sudo apt install xserver-xorg-video-mach64

```
I do expect to work.
Reboot to see the effect .

[INDENT][INDENT]maybe yes ?
[/INDENT][/INDENT]

---

### Post by mk2209 on 2017-03-25
Hello,


install worked, said that it was configured. But still a black Screen after reboot.

---

### Post by Bashing-om on 2017-03-25
mk2209; Yuk !

Does the log file give us any hints ?
```

cat /var/log/Xorg.0.log

```

Does this file exist ?
```

cat /var/log/gpu-manager.log

```
And if so, do we get any hints here ?

[INDENT][INDENT]got to be a reason
[/INDENT][/INDENT]

---

### Post by mk2209 on 2017-03-25
Hello,

Xorg.0.log:
```
[    43.668] 

X.Org X Server 1.18.4

Release Date: 2016-07-19

[    43.669] X Protocol Version 11, Revision 0

[    43.669] Build Operating System: Linux 4.4.0-45-generic i686 Ubuntu

[    43.669] Current Operating System: Linux mk2209-Armada-E500 4.8.0-22-generic #24-Ubuntu SMP Sat Oct 8 09:14:42 UTC 2016 i686

[    43.669] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.8.0-22-generic root=UUID=08e5bcc2-573c-41f3-bfe8-df9c42074e1a ro quiet splash vt.handoff=7

[    43.669] Build Date: 02 November 2016  10:05:40PM

[    43.669] xorg-server 2:1.18.4-1ubuntu6.1 (For technical support please see http://www.ubuntu.com/support) 

[    43.669] Current version of pixman: 0.33.6

[    43.669]     Before reporting problems, check http://wiki.x.org

    to make sure that you have the latest version.

[    43.669] Markers: (--) probed, (**) from config file, (==) default setting,

    (++) from command line, (!!) notice, (II) informational,

    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.

[    43.670] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Mar 26 00:37:17 2017

[    43.691] (==) Using system config directory "/usr/share/X11/xorg.conf.d"

[    43.694] (==) No Layout section.  Using the first Screen section.

[    43.694] (==) No screen section available. Using defaults.

[    43.694] (**) |-->Screen "Default Screen Section" (0)

[    43.694] (**) |   |-->Monitor "<default monitor>"

[    43.730] (==) No monitor specified for screen "Default Screen Section".

    Using a default monitor configuration.

[    43.730] (==) Automatically adding devices

[    43.730] (==) Automatically enabling devices

[    43.731] (==) Automatically adding GPU devices

[    43.731] (==) Max clients allowed: 256, resource mask: 0x1fffff

[    43.731] (WW) The directory "/usr/share/fonts/X11/misc" does not exist.

[    43.731]     Entry deleted from font path.

[    43.731] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.

[    43.731]     Entry deleted from font path.

[    43.731] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.

[    43.731]     Entry deleted from font path.

[    43.731] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.

[    43.731]     Entry deleted from font path.

[    43.731] (WW) The directory "/usr/share/fonts/X11/Type1" does not exist.

[    43.731]     Entry deleted from font path.

[    43.731] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.

[    43.731]     Entry deleted from font path.

[    43.731] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.

[    43.732]     Entry deleted from font path.

[    43.732] (==) FontPath set to:

    built-ins

[    43.732] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"

[    43.732] (II) The server relies on udev to provide the list of input devices.

    If no devices become available, reconfigure udev or disable AutoAddDevices.

[    43.766] (II) Loader magic: 0x80305700

[    43.767] (II) Module ABI versions:

[    43.767]     X.Org ANSI C Emulation: 0.4

[    43.767]     X.Org Video Driver: 20.0

[    43.767]     X.Org XInput driver : 22.1

[    43.767]     X.Org Server Extension : 9.0

[    43.772] (++) using VT number 7

&#12288;

[    43.772] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration

[    43.782] (--) PCI:*(0:1:0:0) 1002:4c4d:0e11:b160 rev 100, Mem @ 0x40000000/16777216, 0x41000000/4096, I/O @ 0x00002000/256, BIOS @ 0x????????/131072

[    43.782] (II) LoadModule: "glx"

[    43.859] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so

[    44.098] (II) Module glx: vendor="X.Org Foundation"

[    44.098]     compiled for 1.18.4, module version = 1.0.0

[    44.098]     ABI class: X.Org Server Extension, version 9.0

[    44.098] (==) AIGLX enabled

[    44.098] (==) Matched ati as autoconfigured driver 0

[    44.098] (==) Matched modesetting as autoconfigured driver 1

[    44.099] (==) Matched fbdev as autoconfigured driver 2

[    44.099] (==) Matched vesa as autoconfigured driver 3

[    44.099] (==) Assigned the driver to the xf86ConfigLayout

[    44.099] (II) LoadModule: "ati"

[    44.100] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so

[    44.100] (II) Module ati: vendor="X.Org Foundation"

[    44.100]     compiled for 1.18.4, module version = 7.7.1

[    44.101]     Module class: X.Org Video Driver

[    44.101]     ABI class: X.Org Video Driver, version 20.0

[    44.101] (II) LoadModule: "mach64"

[    44.101] (II) Loading /usr/lib/xorg/modules/drivers/mach64_drv.so

[    44.206] (II) Module mach64: vendor="X.Org Foundation"

[    44.207]     compiled for 1.18.1, module version = 6.9.5

[    44.207]     Module class: X.Org Video Driver

[    44.207]     ABI class: X.Org Video Driver, version 20.0

[    44.207] (II) LoadModule: "modesetting"

[    44.209] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so

[    44.210] (II) Module modesetting: vendor="X.Org Foundation"

[    44.210]     compiled for 1.18.4, module version = 1.18.4

[    44.210]     Module class: X.Org Video Driver

[    44.210]     ABI class: X.Org Video Driver, version 20.0

[    44.210] (II) LoadModule: "fbdev"

[    44.211] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so

[    44.216] (II) Module fbdev: vendor="X.Org Foundation"

[    44.220]     compiled for 1.18.1, module version = 0.4.4

[    44.220]     Module class: X.Org Video Driver

[    44.220]     ABI class: X.Org Video Driver, version 20.0

[    44.220] (II) LoadModule: "vesa"

[    44.221] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so

[    44.221] (II) Module vesa: vendor="X.Org Foundation"

[    44.221]     compiled for 1.18.1, module version = 2.3.4

[    44.222]     Module class: X.Org Video Driver

[    44.222]     ABI class: X.Org Video Driver, version 20.0

[    44.222] (II) MACH64: Driver for ATI Mach64 chipsets

[    44.222] (II) modesetting: Driver for Modesetting Kernel Drivers: kms

[    44.222] (II) FBDEV: driver for framebuffer: fbdev

[    44.222] (II) VESA: driver for VESA chipsets: vesa

[    44.223] (WW) Falling back to old probe method for modesetting

[    44.223] (EE) open /dev/dri/card0: No such file or directory

[    44.223] (WW) Falling back to old probe method for fbdev

[    44.223] (II) Loading sub module "fbdevhw"

[    44.223] (II) LoadModule: "fbdevhw"

[    44.224] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so

[    44.225] (II) Module fbdevhw: vendor="X.Org Foundation"

[    44.225]     compiled for 1.18.4, module version = 0.0.2

[    44.225]     ABI class: X.Org Video Driver, version 20.0

[    44.225] (WW) Falling back to old probe method for vesa

[    44.226] (II) MACH64(0): Creating default Display subsection in Screen section

    "Default Screen Section" for depth/fbbpp 24/32

[    44.226] (==) MACH64(0): Depth 24, (--) framebuffer bpp 32

[    44.226] (==) MACH64(0): Using XAA acceleration architecture

[    44.226] (II) MACH64: Mach64 in slot 1:0:0 detected.

[    44.226] (II) Loading sub module "vbe"

[    44.226] (II) LoadModule: "vbe"

[    44.227] (II) Loading /usr/lib/xorg/modules/libvbe.so

[    44.231] (II) Module vbe: vendor="X.Org Foundation"

[    44.231]     compiled for 1.18.4, module version = 1.1.0

[    44.232]     ABI class: X.Org Video Driver, version 20.0

[    44.232] (II) Loading sub module "int10"

[    44.232] (II) LoadModule: "int10"

[    44.233] (II) Loading /usr/lib/xorg/modules/libint10.so

[    44.250] (II) Module int10: vendor="X.Org Foundation"

[    44.250]     compiled for 1.18.4, module version = 1.0.0

[    44.250]     ABI class: X.Org Video Driver, version 20.0

[    44.250] (II) MACH64(0): initializing int10

[    44.252] (II) MACH64(0): Primary V_BIOS segment is: 0xc000

[    44.253] (II) MACH64(0): VESA BIOS detected

[    44.254] (II) MACH64(0): VESA VBE Version 2.0

[    44.254] (II) MACH64(0): VESA VBE Total Mem: 8128 kB

[    44.254] (II) MACH64(0): VESA VBE OEM: ATI MACH64

[    44.254] (II) MACH64(0): VESA VBE OEM Software Rev: 1.0

[    44.254] (II) MACH64(0): VESA VBE OEM Vendor: ATI Technologies Inc.

[    44.254] (II) MACH64(0): VESA VBE OEM Product: MACH64RM

[    44.254] (II) MACH64(0): VESA VBE OEM Product Rev: 01.00

[    44.257] (II) MACH64(0): VESA VBE DDC supported

[    44.257] (II) MACH64(0): VESA VBE DDC Level none

[    44.257] (II) MACH64(0): VESA VBE DDC transfer in appr. 2 sec.

[    44.265] (II) MACH64(0): VESA VBE DDC read failed

[    44.269] (--) MACH64(0): Panel model Samsung LT141X7-122.

[    44.269] (II) MACH64(0): BIOS Data:  BIOSSize=0x10000, ROMTable=0x010E.

[    44.269] (II) MACH64(0): BIOS Data:  ClockTable=0x0A8C, FrequencyTable=0x0000.

[    44.269] (II) MACH64(0): BIOS Data:  LCDTable=0x0180.

[    44.269] (II) MACH64(0): BIOS Data:  VideoTable=0x0000, HardwareTable=0x015E.

[    44.269] (II) MACH64(0): BIOS Data:  I2CType=0x0F, Tuner=0x00, Decoder=0x00, Audio=0x0F.

[    44.269] (--) MACH64(0): ATI 3D Rage Mobility graphics controller detected.

[    44.269] (--) MACH64(0): Chip type 4C4D "LM", version 4, foundry TSMC, class 0, revision 0x01.

[    44.269] (--) MACH64(0): AGP bus interface detected;  block I/O base is 0x2000.

[    44.269] (--) MACH64(0): ATI Mach64 adapter detected.

[    44.269] (!!) MACH64(0): For information on using the multimedia capabilities

    of this adapter, please see http://gatos.sf.net.

[    44.269] (--) MACH64(0): Internal RAMDAC (subtype 1) detected.

[    44.270] (==) MACH64(0): RGB weight 888

[    44.270] (==) MACH64(0): Default visual is TrueColor

[    44.270] (==) MACH64(0): Using gamma correction (1.0, 1.0, 1.0)

[    44.270] (II) MACH64(0): Using Mach64 accelerator CRTC.

[    44.270] (--) MACH64(0): 1024x768 panel (ID 11) detected.

[    44.270] (--) MACH64(0): Panel clock is 65.146 MHz.

[    44.270] (II) MACH64(0): Using digital flat panel interface.

[    44.270] (II) MACH64(0): Storing hardware cursor image at 0x407FFC00.

[    44.270] (II) MACH64(0): Using 8 MB linear aperture at 0x40000000.

[    44.270] (!!) MACH64(0): Virtual resolutions will be limited to 8191 kB

 due to linear aperture size and/or placement of hardware cursor image area.

[    44.270] (II) MACH64(0): Using Block 0 MMIO aperture at 0x41000400.

[    44.270] (II) MACH64(0): Using Block 1 MMIO aperture at 0x41000000.

[    44.276] (II) MACH64(0): MMIO write caching enabled.

[    44.277] (--) MACH64(0): 8192 kB of SDRAM (1:1) detected (using 8191 kB).

[    44.277] (WW) MACH64(0): Cannot shadow an accelerated frame buffer.

[    44.277] (II) MACH64(0): Engine XCLK 124.453 MHz;  Refresh rate code 12.

[    44.277] (--) MACH64(0): Internal programmable clock generator detected.

[    44.277] (--) MACH64(0): Reference clock 29.500 MHz.

[    44.277] (WW) MACH64(0): Unable to estimate virtual size

[    44.277] (II) MACH64(0): Maximum clock: 230.00 MHz

[    44.277] (II) MACH64(0): Not using default mode "1152x864" (exceeds panel dimensions)

[    44.277] (II) MACH64(0): Not using default mode "576x432" (exceeds panel dimensions)

[    44.278] (II) MACH64(0): Not using default mode "1280x960" (exceeds panel dimensions)

[    44.278] (II) MACH64(0): Not using default mode "640x480" (exceeds panel dimensions)

[    44.278] (II) MACH64(0): Not using default mode "1280x960" (exceeds panel dimensions)

[    44.278] (II) MACH64(0): Not using default mode "640x480" (exceeds panel dimensions)

[    44.278] (II) MACH64(0): Not using default mode "1280x1024" (exceeds panel dimensions)

[    44.278] (II) MACH64(0): Not using default mode "640x512" (exceeds panel dimensions)

[    44.278] (II) MACH64(0): Not using default mode "1280x1024" (exceeds panel dimensions)

[    44.278] (II) MACH64(0): Not using default mode "640x512" (exceeds panel dimensions)

[    44.278] (II) MACH64(0): Not using default mode "1280x1024" (exceeds panel dimensions)

[    44.278] (II) MACH64(0): Not using default mode "640x512" (exceeds panel dimensions)

[    44.278] (II) MACH64(0): Not using default mode "1600x1200" (exceeds panel dimensions)

[    44.278] (II) MACH64(0): Not using default mode "800x600" (exceeds panel dimensions)

[    44.278] (II) MACH64(0): Not using default mode "1600x1200" (exceeds panel dimensions)

[    44.278] (II) MACH64(0): Not using default mode "800x600" (exceeds panel dimensions)

[    44.278] (II) MACH64(0): Not using default mode "1600x1200" (exceeds panel dimensions)

[    44.278] (II) MACH64(0): Not using default mode "800x600" (exceeds panel dimensions)

[    44.279] (II) MACH64(0): Not using default mode "1600x1200" (exceeds panel dimensions)

[    44.279] (II) MACH64(0): Not using default mode "800x600" (exceeds panel dimensions)

[    44.279] (II) MACH64(0): Not using default mode "1600x1200" (exceeds panel dimensions)

[    44.279] (II) MACH64(0): Not using default mode "800x600" (exceeds panel dimensions)

[    44.279] (II) MACH64(0): Not using default mode "1792x1344" (insufficient memory for mode)

[    44.279] (II) MACH64(0): Not using default mode "896x672" (exceeds panel dimensions)

[    44.279] (II) MACH64(0): Not using default mode "1792x1344" (insufficient memory for mode)

[    44.279] (II) MACH64(0): Not using default mode "896x672" (exceeds panel dimensions)

[    44.279] (II) MACH64(0): Not using default mode "1856x1392" (insufficient memory for mode)

[    44.279] (II) MACH64(0): Not using default mode "928x696" (exceeds panel dimensions)

[    44.279] (II) MACH64(0): Not using default mode "1856x1392" (insufficient memory for mode)

[    44.279] (II) MACH64(0): Not using default mode "928x696" (exceeds panel dimensions)

[    44.279] (II) MACH64(0): Not using default mode "1920x1440" (insufficient memory for mode)

[    44.279] (II) MACH64(0): Not using default mode "960x720" (exceeds panel dimensions)

[    44.279] (II) MACH64(0): Not using default mode "1920x1440" (insufficient memory for mode)

[    44.279] (II) MACH64(0): Not using default mode "960x720" (exceeds panel dimensions)

[    44.279] (II) MACH64(0): Not using default mode "1152x864" (exceeds panel dimensions)

[    44.283] (II) MACH64(0): Not using default mode "576x432" (exceeds panel dimensions)

[    44.283] (II) MACH64(0): Not using default mode "1152x864" (exceeds panel dimensions)

[    44.283] (II) MACH64(0): Not using default mode "576x432" (exceeds panel dimensions)

[    44.283] (II) MACH64(0): Not using default mode "1152x864" (exceeds panel dimensions)

[    44.283] (II) MACH64(0): Not using default mode "576x432" (exceeds panel dimensions)

[    44.283] (II) MACH64(0): Not using default mode "1152x864" (exceeds panel dimensions)

[    44.285] (II) MACH64(0): Not using default mode "576x432" (exceeds panel dimensions)

[    44.285] (II) MACH64(0): Not using default mode "1152x864" (exceeds panel dimensions)

[    44.285] (II) MACH64(0): Not using default mode "576x432" (exceeds panel dimensions)

[    44.285] (II) MACH64(0): Not using default mode "1152x864" (exceeds panel dimensions)

[    44.285] (II) MACH64(0): Not using default mode "576x432" (exceeds panel dimensions)

[    44.285] (II) MACH64(0): Not using default mode "1360x768" (exceeds panel dimensions)

[    44.285] (II) MACH64(0): Not using default mode "1360x768" (exceeds panel dimensions)

[    44.286] (II) MACH64(0): Not using default mode "1400x1050" (exceeds panel dimensions)

[    44.286] (II) MACH64(0): Not using default mode "700x525" (exceeds panel dimensions)

[    44.286] (II) MACH64(0): Not using default mode "1400x1050" (exceeds panel dimensions)

[    44.286] (II) MACH64(0): Not using default mode "700x525" (exceeds panel dimensions)

[    44.286] (II) MACH64(0): Not using default mode "1400x1050" (exceeds panel dimensions)

[    44.286] (II) MACH64(0): Not using default mode "700x525" (exceeds panel dimensions)

[    44.286] (II) MACH64(0): Not using default mode "1400x1050" (exceeds panel dimensions)

[    44.286] (II) MACH64(0): Not using default mode "700x525" (exceeds panel dimensions)

[    44.286] (II) MACH64(0): Not using default mode "1440x900" (exceeds panel dimensions)

[    44.286] (II) MACH64(0): Not using default mode "720x450" (exceeds panel dimensions)

[    44.286] (II) MACH64(0): Not using default mode "1600x1024" (exceeds panel dimensions)

[    44.286] (II) MACH64(0): Not using default mode "800x512" (exceeds panel dimensions)

[    44.286] (II) MACH64(0): Not using default mode "1680x1050" (exceeds panel dimensions)

[    44.286] (II) MACH64(0): Not using default mode "840x525" (exceeds panel dimensions)

[    44.286] (II) MACH64(0): Not using default mode "1680x1050" (exceeds panel dimensions)

[    44.286] (II) MACH64(0): Not using default mode "840x525" (exceeds panel dimensions)

[    44.287] (II) MACH64(0): Not using default mode "1680x1050" (exceeds panel dimensions)

[    44.287] (II) MACH64(0): Not using default mode "840x525" (exceeds panel dimensions)

[    44.287] (II) MACH64(0): Not using default mode "1680x1050" (exceeds panel dimensions)

[    44.287] (II) MACH64(0): Not using default mode "840x525" (exceeds panel dimensions)

[    44.287] (II) MACH64(0): Not using default mode "1680x1050" (exceeds panel dimensions)

[    44.287] (II) MACH64(0): Not using default mode "840x525" (exceeds panel dimensions)

[    44.287] (II) MACH64(0): Not using default mode "1920x1080" (exceeds panel dimensions)

[    44.287] (II) MACH64(0): Not using default mode "960x540" (exceeds panel dimensions)

[    44.287] (II) MACH64(0): Not using default mode "1920x1200" (insufficient memory for mode)

[    44.287] (II) MACH64(0): Not using default mode "960x600" (exceeds panel dimensions)

[    44.287] (II) MACH64(0): Not using default mode "1920x1440" (insufficient memory for mode)

[    44.287] (II) MACH64(0): Not using default mode "960x720" (exceeds panel dimensions)

[    44.287] (II) MACH64(0): Not using default mode "2048x1536" (insufficient memory for mode)

[    44.287] (II) MACH64(0): Not using default mode "1024x768" (exceeds panel dimensions)

[    44.287] (II) MACH64(0): Not using default mode "2048x1536" (insufficient memory for mode)

[    44.287] (II) MACH64(0): Not using default mode "1024x768" (exceeds panel dimensions)

[    44.287] (II) MACH64(0): Not using default mode "2048x1536" (insufficient memory for mode)

[    44.292] (II) MACH64(0): Not using default mode "1024x768" (exceeds panel dimensions)

[    44.292] (--) MACH64(0): Virtual size is 1024x768 (pitch 1024)

[    44.292] (**) MACH64(0): *Default mode "1024x768i": 44.9 MHz, 35.5 kHz, 86.9 Hz (I)

[    44.292] (II) MACH64(0): Modeline "1024x768i"x86.9   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz zd)

[    44.293] (**) MACH64(0): *Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz

[    44.293] (II) MACH64(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz zd)

[    44.293] (**) MACH64(0): *Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz

[    44.293] (II) MACH64(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz zd)

[    44.293] (**) MACH64(0): *Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz

[    44.293] (II) MACH64(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz zd)

[    44.293] (**) MACH64(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz

[    44.293] (II) MACH64(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz zd)

[    44.293] (**) MACH64(0): *Built-in mode "Native panel mode": 65.1 MHz, 62.6 kHz, 81.4 Hz

[    44.293] (II) MACH64(0): Modeline "Native panel mode"x81.4   65.15  1024 1024 1032 1040  768 768 769 770 (62.6 kHz zb)

[    44.293] (**) MACH64(0): *Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz

[    44.293] (II) MACH64(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz zd)

[    44.293] (**) MACH64(0): *Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz

[    44.293] (II) MACH64(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz zd)

[    44.294] (**) MACH64(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz

[    44.294] (II) MACH64(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz zd)

[    44.294] (**) MACH64(0): *Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz

[    44.294] (II) MACH64(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz zd)

[    44.294] (**) MACH64(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz

[    44.294] (II) MACH64(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz zd)

[    44.294] (**) MACH64(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz

[    44.294] (II) MACH64(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz zd)

[    44.294] (**) MACH64(0): *Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz

[    44.294] (II) MACH64(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz zd)

[    44.294] (**) MACH64(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz

[    44.294] (II) MACH64(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz zd)

[    44.294] (**) MACH64(0): *Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz

[    44.294] (II) MACH64(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz zd)

[    44.295] (**) MACH64(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz

[    44.295] (II) MACH64(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz zd)

[    44.295] (**) MACH64(0): *Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz

[    44.295] (II) MACH64(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz zd)

[    44.295] (**) MACH64(0): *Default mode "680x384": 36.0 MHz, 47.4 kHz, 60.0 Hz (D)

[    44.295] (II) MACH64(0): Modeline "680x384"x60.0   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz zd)

[    44.295] (**) MACH64(0): *Default mode "680x384": 42.4 MHz, 47.7 kHz, 59.8 Hz (D)

[    44.295] (II) MACH64(0): Modeline "680x384"x59.8   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz zd)

[    44.295] (**) MACH64(0): *Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz

[    44.295] (II) MACH64(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz zd)

[    44.295] (**) MACH64(0): *Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz

[    44.295] (II) MACH64(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz zd)

[    44.295] (**) MACH64(0): *Default mode "512x384i": 22.4 MHz, 35.5 kHz, 86.6 Hz (D)

[    44.295] (II) MACH64(0): Modeline "512x384i"x86.6   22.45  512 516 604 632  384 384 388 409 interlace doublescan +hsync +vsync (35.5 kHz zd)

[    44.300] (**) MACH64(0): *Default mode "512x384": 47.2 MHz, 68.7 kHz, 85.0 Hz (D)

[    44.300] (II) MACH64(0): Modeline "512x384"x85.0   47.25  512 536 584 688  384 384 386 404 doublescan +hsync +vsync (68.7 kHz zd)

[    44.300] (**) MACH64(0): *Default mode "512x384": 39.4 MHz, 60.0 kHz, 75.0 Hz (D)

[    44.300] (II) MACH64(0): Modeline "512x384"x75.0   39.38  512 520 568 656  384 384 386 400 doublescan +hsync +vsync (60.0 kHz zd)

[    44.300] (**) MACH64(0): *Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)

[    44.300] (II) MACH64(0): Modeline "512x384"x70.1   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync (56.5 kHz zd)

[    44.300] (**) MACH64(0): *Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)

[    44.300] (II) MACH64(0): Modeline "512x384"x60.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz zd)

[    44.300] (**) MACH64(0): *Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)

[    44.300] (II) MACH64(0): Modeline "416x312"x74.7   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync (49.7 kHz zd)

[    44.301] (**) MACH64(0): *Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)

[    44.301] (II) MACH64(0): Modeline "400x300"x85.3   28.15  400 416 448 524  300 300 302 315 doublescan +hsync +vsync (53.7 kHz zd)

[    44.301] (**) MACH64(0): *Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)

[    44.301] (II) MACH64(0): Modeline "400x300"x75.1   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync (46.9 kHz zd)

[    44.301] (**) MACH64(0): *Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)

[    44.301] (II) MACH64(0): Modeline "400x300"x72.2   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync (48.1 kHz zd)

[    44.301] (**) MACH64(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)

[    44.301] (II) MACH64(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz zd)

[    44.301] (**) MACH64(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)

[    44.301] (II) MACH64(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz zd)

[    44.301] (**) MACH64(0): *Default mode "320x240": 18.0 MHz, 43.3 kHz, 85.2 Hz (D)

[    44.301] (II) MACH64(0): Modeline "320x240"x85.2   18.00  320 348 376 416  240 240 242 254 doublescan -hsync -vsync (43.3 kHz zd)

[    44.301] (**) MACH64(0): *Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)

[    44.302] (II) MACH64(0): Modeline "320x240"x75.0   15.75  320 328 360 420  240 240 242 250 doublescan -hsync -vsync (37.5 kHz zd)

[    44.302] (**) MACH64(0): *Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)

[    44.302] (II) MACH64(0): Modeline "320x240"x72.8   15.75  320 332 352 416  240 244 246 260 doublescan -hsync -vsync (37.9 kHz zd)

[    44.302] (**) MACH64(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)

[    44.302] (II) MACH64(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz zd)

[    44.302] (**) MACH64(0): *Default mode "360x200": 17.8 MHz, 37.9 kHz, 85.0 Hz (D)

[    44.302] (II) MACH64(0): Modeline "360x200"x85.0   17.75  360 378 414 468  200 200 202 223 doublescan -hsync +vsync (37.9 kHz zd)

[    44.302] (**) MACH64(0): *Default mode "320x200": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)

[    44.302] (II) MACH64(0): Modeline "320x200"x85.3   15.75  320 336 368 416  200 200 202 222 doublescan -hsync +vsync (37.9 kHz zd)

[    44.302] (**) MACH64(0): *Default mode "320x175": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)

[    44.302] (II) MACH64(0): Modeline "320x175"x85.3   15.75  320 336 368 416  175 191 192 222 doublescan +hsync -vsync (37.9 kHz zd)

[    44.302] (==) MACH64(0): DPI set to (96, 96)

[    44.302] (II) Loading sub module "fb"

[    44.302] (II) LoadModule: "fb"

[    44.303] (II) Loading /usr/lib/xorg/modules/libfb.so

[    44.311] (II) Module fb: vendor="X.Org Foundation"

[    44.311]     compiled for 1.18.4, module version = 1.0.0

[    44.311]     ABI class: X.Org ANSI C Emulation, version 0.4

[    44.311] (II) Loading sub module "ramdac"

[    44.311] (II) LoadModule: "ramdac"

[    44.313] (II) Module "ramdac" already built-in

[    44.313] (II) Loading sub module "i2c"

[    44.313] (II) LoadModule: "i2c"

[    44.313] (II) Module "i2c" already built-in

[    44.313] (II) MACH64(0): I2C bus "Mach64" initialized.

[    44.314] (II) UnloadModule: "modesetting"

[    44.314] (II) Unloading modesetting

[    44.314] (II) UnloadModule: "fbdev"

[    44.314] (II) Unloading fbdev

[    44.314] (II) UnloadSubModule: "fbdevhw"

[    44.314] (II) Unloading fbdevhw

[    44.315] (II) UnloadModule: "vesa"

[    44.315] (II) Unloading vesa

[    44.315] (--) Depth 24 pixmap format is 32 bpp

[    44.344] (II) MACH64(0): [drm] SAREA 2200+1208: 3408

[    44.344] drmOpenDevice: node name is /dev/dri/card0

[    44.351] drmOpenDevice: node name is /dev/dri/card0

[    44.389] [drm] failed to load kernel module "mach64"

c[    44.399] (EE) [drm] drmOpen failed.

[    44.400] (EE) MACH64(0): [dri] DRIScreenInit Failed

[    44.419] (==) MACH64(0): Backing store enabled

[    44.433] (==) MACH64(0): Silken mouse enabled

[    44.441] (==) MACH64(0): DPMS enabled

[    44.441] (II) MACH64(0): Direct rendering disabled

[    44.443] (==) RandR enabled

[    44.724] (II) SELinux: Disabled on system

[    44.733] (II) AIGLX: Screen 0 is not DRI2 capable

[    44.733] (EE) AIGLX: reverting to software rendering

[    46.225] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer

[    46.240] (II) AIGLX: Loaded and initialized swrast

[    46.241] (II) GLX: Initialized DRISWRAST GL provider for screen 0

[    46.566] (II) config/udev: Adding input device Power Button (/dev/input/event2)

[    46.567] (**) Power Button: Applying InputClass "evdev keyboard catchall"

[    46.567] (II) LoadModule: "evdev"

[    46.568] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so

[    46.602] (II) Module evdev: vendor="X.Org Foundation"

[    46.602]     compiled for 1.18.3, module version = 2.10.2

[    46.602]     Module class: X.Org XInput Driver

[    46.602]     ABI class: X.Org XInput driver, version 22.1

[    46.602] (II) Using input driver 'evdev' for 'Power Button'

[    46.602] (**) Power Button: always reports core events

[    46.603] (**) evdev: Power Button: Device: "/dev/input/event2"

[    46.603] (--) evdev: Power Button: Vendor 0 Product 0x1

[    46.603] (--) evdev: Power Button: Found keys

[    46.603] (II) evdev: Power Button: Configuring as keyboard

[    46.604] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"

[    46.604] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)

[    46.604] (**) Option "xkb_rules" "evdev"

[    46.604] (**) Option "xkb_model" "pc105"

[    46.604] (**) Option "xkb_layout" "de"

[    46.811] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)

[    46.820] (II) No input driver specified, ignoring this device.

[    46.821] (II) This device may have been added with another device file.

[    46.823] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)

[    46.823] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"

[    46.823] (II) Using input driver 'evdev' for 'Sleep Button'

[    46.823] (**) Sleep Button: always reports core events

[    46.828] (**) evdev: Sleep Button: Device: "/dev/input/event0"

[    46.828] (--) evdev: Sleep Button: Vendor 0 Product 0x3

[    46.828] (--) evdev: Sleep Button: Found keys

[    46.829] (II) evdev: Sleep Button: Configuring as keyboard

[    46.829] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0/event0"

[    46.829] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 7)

[    46.829] (**) Option "xkb_rules" "evdev"

[    46.829] (**) Option "xkb_model" "pc105"

[    46.829] (**) Option "xkb_layout" "de"

[    46.837] (II) config/udev: Adding input device ES1978 (/dev/input/event5)

[    46.837] (**) ES1978: Applying InputClass "evdev keyboard catchall"

[    46.837] (II) Using input driver 'evdev' for 'ES1978'

[    46.837] (**) ES1978: always reports core events

[    46.838] (**) evdev: ES1978: Device: "/dev/input/event5"

[    46.838] (--) evdev: ES1978: Vendor 0x125d Product 0x1978

[    46.838] (--) evdev: ES1978: Found keys

[    46.838] (II) evdev: ES1978: Configuring as keyboard

[    46.838] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:08.0/input/input12/event5"

[    46.838] (II) XINPUT: Adding extended input device "ES1978" (type: KEYBOARD, id 8)

[    46.838] (**) Option "xkb_rules" "evdev"

[    46.838] (**) Option "xkb_model" "pc105"

[    46.838] (**) Option "xkb_layout" "de"

[    46.875] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)

[    46.876] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"

[    46.876] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'

[    46.876] (**) AT Translated Set 2 keyboard: always reports core events

[    46.876] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"

[    46.877] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1

[    46.877] (--) evdev: AT Translated Set 2 keyboard: Found keys

[    46.877] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard

[    46.877] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"

[    46.877] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)

[    46.877] (**) Option "xkb_rules" "evdev"

[    46.877] (**) Option "xkb_model" "pc105"

[    46.877] (**) Option "xkb_layout" "de"

[    46.887] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event4)

[    46.887] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"

[    46.887] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"

[    46.894] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"

[    46.894] (II) LoadModule: "synaptics"

[    46.895] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so

[    46.903] (II) Module synaptics: vendor="X.Org Foundation"

[    46.903]     compiled for 1.18.3, module version = 1.8.3

[    46.903]     Module class: X.Org XInput Driver

[    46.903]     ABI class: X.Org XInput driver, version 22.1

[    46.903] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'

[    46.903] (**) SynPS/2 Synaptics TouchPad: always reports core events

[    46.908] (**) Option "Device" "/dev/input/event4"

[    46.909] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472 (res 85)

[    46.909] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448 (res 94)

[    46.909] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255

[    46.909] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15

[    46.909] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple

[    46.909] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7

[    46.909] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found

[    46.909] (**) SynPS/2 Synaptics TouchPad: always reports core events

[    46.910] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input11/event4"

[    46.910] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 10)

[    46.910] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5

[    46.910] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75

[    46.910] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.040

[    46.911] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1

[    46.911] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1

[    46.911] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000

[    46.911] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4

[    46.911] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found

[    46.924] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)

[    46.924] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"

```

gpu-manager.log does exist:
```
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-nvidia-was-loaded file
can't access /run/u-d-c-fglrx-was-loaded file
Looking for fglrx modules in /lib/modules/4.8.0-22-generic/updates/dkms
Looking for nvidia modules in /lib/modules/4.8.0-22-generic/updates/dkms
Is nvidia loaded? no
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is fglrx loaded? no
Was fglrx unloaded? no
Is fglrx blacklisted? no
Is intel loaded? no
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is nouveau loaded? no
Is nouveau blacklisted? no
Is fglrx kernel module available? no
Is nvidia kernel module available? no
Vendor/Device Id: 1002:4c4d
BusID "PCI:1@0:0:0"
Is boot vga? yes
Error: can't access /sys/bus/pci/devices/0000:01:00.0/driver
The device is not bound to any driver. Skipping...
Error : Failed to open /dev/dri
Error : Failed to open /dev/dri
Error : Failed to open /dev/dri
Error : Failed to open /dev/dri
Does it require offloading? no
last cards number = 0
Has amd? no
Has intel? no
Has nvidia? no
How many cards? 0
Has the system changed? No
main_arch_path i386-linux-gnu, other_arch_path x86_64-linux-gnu
Current alternative: /usr/lib/i386-linux-gnu/mesa/ld.so.conf
Current core alternative: (null)
Current egl alternative: /usr/lib/i386-linux-gnu/mesa-egl/ld.so.conf
Is nvidia enabled? no
Is nvidia egl enabled? no
Is fglrx enabled? no
Is mesa enabled? yes
Is mesa egl enabled? yes
Is pxpress enabled? no
Is prime enabled? no
Is prime egl enabled? no
Is nvidia available? no
Is nvidia egl available? no
Is fglrx available? no
Is fglrx-core available? no
Is mesa available? yes
Is mesa egl available? yes
Is pxpress available? no
Is prime available? no
Is prime egl available? no

```

---

### Post by Bashing-om on 2017-03-25
mk2209; Hummm ..

I have been beating my head against this some more .
We still are missing a piece to the puzzle:
> 
44.226] (II) MACH64: Mach64 in slot 1:0:0 detected.

44.344] (II) MACH64(0): [drm] SAREA 2200+1208: 3408

[    44.344] drmOpenDevice: node name is /dev/dri/card0

[    44.351] drmOpenDevice: node name is /dev/dri/card0

[    44.389] [drm] failed to load kernel module "mach64"

c[    44.399] (EE) [drm] drmOpen failed.

[    44.400] (EE) MACH64(0): [dri] DRIScreenInit Failed

45.798] (EE) Failed to load module "mach64" (module does not exist, 0)

-bk-

Vendor/Device Id: 1002:4c4d
BusID "PCI:1@0:0:0"
Is boot vga? yes
Error: can't access /sys/bus/pci/devices/0000:01:00.0/driver
The device is not bound to any driver. Skipping...
Error : Failed to open /dev/dri
Error : Failed to open /dev/dri
Error : Failed to open /dev/dri
Error : Failed to open /dev/dri


There's bunches here I do not understand - I am in my learning mode and trying to find out .

[INDENT][INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2017-03-26
mk2209;  Welp;

Not making much headway here - Lots I just do not know about the ATI/mach64 driver interface .
For lack of a better option presently, do we require that the headers for the booted kernel be installed to build the module ?
What have we installed:
```

uname -r
ls -al /usr/src/

```

We try and identify the missing piece .

[INDENT][INDENT]sometimes I wonder
[INDENT][INDENT][INDENT]other times I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mk2209 on 2017-03-26
Hello,


```
4.8.0-22-generic



a total of 24

drwxr-xr-x  6 root root 4096 MÃ¤r 21 18:44 .

drwxr-xr-x 11 root root 4096 Okt 12 21:26 ..

drwxr-xr-x 27 root root 4096 Okt 12 21:27 linux-headers-4.8.0-22

drwxr-xr-x  7 root root 4096 Okt 12 21:27 linux-headers-4.8.0-22-generic

drwxr-xr-x 27 root root 4096 MÃ¤r 21 18:44 linux-headers-4.8.0-41

drwxr-xr-x  7 root root 4096 MÃ¤r 21 18:44 linux-headers-4.8.0-41-generic

```

---

### Post by Bashing-om on 2017-03-26
mk2209; Hummmm ...

Well, not having the headers for the kernels IS NOT the issue .

I am not at all sure what to think as I see what I perceive as conflicting info:
"apt show xserver-xorg-video-ati"
> 
 Users of Rage, Mach, or Radeon boards may remove this package only if
 they use Driver "r128", "mach64", or "radeon" in /etc/X11/xorg.conf
 instead of relying on autodetection.
 - ubuntu does the autodetection ! -
But :
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati-lts-xenial/+bug/1611982](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati-lts-xenial/+bug/1611982)
> 

This bug was fixed in the package xserver-xorg-video-ati-lts-xenial - 1:7.7.0-1~trusty2

---------------
xserver-xorg-video-ati-lts-xenial (1:7.7.0-1~trusty2) trusty; urgency=medium

  * control: Move mach64, r128 back to Depends. (LP: #1611982)

-bk-
The verification of the Stable Release Update for xserver-xorg-video-ati-lts-xenial has completed successfully and the package has now been released to -updates.


My think'n is that both the xserver-xorg-video-r128 and xserver-xorg-video-ati need to be installed ???

what shows booted with the -22 kernel:
```

dpkg -l xserver-xorg-video-mach64 xserver-xorg-video-r128 xserver-xorg-video-ati

```
compared to booting the -41 kernel ( clt+alt+F1 @ login screen ) ,

The -41 install is missing something that is present in the -22 install.

[INDENT][INDENT]still, just do not know
[/INDENT][/INDENT]

---

### Post by mk2209 on 2017-03-27
Hello,

cannot press ctrl+alt+f1 as the System hangs before the login screen appears. So I have booted -41 kernel into recovery mode and started the shell to put in the dpkg-command. 

I get exact the same output as with -22 kernel:
```
||/ Name           Version      Architektur  Beschreibung
+++-==============-============-============-=================================
ii  xserver-xorg-v 1:7.7.1-1    i386         X.Org X server -- AMD/ATI display
ii  xserver-xorg-v 6.9.5-1build i386         X.Org X server -- ATI Mach64 disp
un  xserver-xorg-v <none>      <none>      (no description available)

```

---

### Post by Bashing-om on 2017-03-28
mk2209; Sorry;

To say; but I am just flat stuck . It is now above my skill set to know how to proceed further.
I do hope some on can come to our rescue and advise better .

[INDENT][INDENT]sometimes I just do not know
[/INDENT][/INDENT]

---

### Post by mk2209 on 2017-04-01
Hello Bashing-Om,

I have now reinstalled the Linux and after I did the Updates, it hangs again. But I think it has nothing to do with the graphic-card, because now I can get to the login screen and first, a few seconds after login, it will crash. Only background image and the mouse cursor stops to move.

I need the laptop especially for a certain program to work, so It doesn't mind much if I work with an older kernel. I have removed the faulty kernel  with "[COLOR=#3366FF]sudo apt-get remove --purge linux-image[/COLOR]..." and the computer works now.

However, many thanks Bashing-Om for trying to help me.

mk2209

---

