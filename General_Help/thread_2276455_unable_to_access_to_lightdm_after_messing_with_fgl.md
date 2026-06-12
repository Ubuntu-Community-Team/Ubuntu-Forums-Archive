---
title: "unable to access to lightdm after messing with fglrx drivers and screwing up Xorg"
date: 2015-05-02
forum: General Help
---

### Post by sangimed on 2015-05-02
[COLOR=#111111][FONT=Ubuntu]I recently removed the fglrx driver from my ubuntu 14.04.2 laptop computer after noticing that it's not really good for the battery life.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]But after restarting I ended up with this screen (after the loading ubuntu logo):

[ATTACH=CONFIG]261723[/ATTACH]

[/FONT][/COLOR]
Content of `/etc/x11/xorg.conf`:

```

Section "ServerLayout"
    Identifier "amd-layout"
    Screen 0 "amd-screen" 0 0
EndSection


Section "Device"
    Identifier "intel"
    Driver "intel"
    Option "AccelMethod" "uxa"
    BusID "PCI:0@0:2:0"
EndSection


Section "Device"
    Identifier "amd-device"
    Driver "fglrx"
    BusID "PCI:1:0:0"
EndSection


Section "Monitor"
    Identifier "amd-monitor"
    Option "VendorName" "ATI Proprietary Driver"
    Option "ModelName" "Generic Autodetecting Monitor"
    Option "DPMS" "true"
EndSection


Section "Screen"
    Identifier "amd-screen"
    Device "amd-device"
    Monitor "amd-monitor"
    DefaultDepth 24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection



```

Content of '/var/log/Xorg.0.log' :

```

[   158.865] 
X.Org X Server 1.16.0
Release Date: 2014-07-16
[   158.867] X Protocol Version 11, Revision 0
[   158.868] Build Operating System: Linux 3.2.0-70-generic x86_64 Ubuntu
[   158.871] Current Operating System: Linux 7h3 3.16.0-34-generic #47~14.04.1-Ubuntu SMP Fri Apr 10 17:49:16 UTC 2015 x86_64
[   158.871] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-34-generic root=UUID=13222574-b16d-4bf4-97ee-19702a7c2746 ro quiet splash vt.handoff=7
[   158.875] Build Date: 12 February 2015  02:46:23PM
[   158.877] xorg-server 2:1.16.0-1ubuntu1.3 (For technical support please see http://www.ubuntu.com/support) 
[   158.877] Current version of pixman: 0.30.2
[   158.880]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   158.880] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   158.886] (==) Log file: "/var/log/Xorg.0.log", Time: Sat May  2 18:06:29 2015
[   158.887] (==) Using config file: "/etc/X11/xorg.conf"
[   158.888] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   158.888] (==) ServerLayout "amd-layout"
[   158.888] (**) |-->Screen "amd-screen" (0)
[   158.888] (**) |   |-->Monitor "amd-monitor"
[   158.889] (**) |   |-->Device "amd-device"
[   158.889] (==) Automatically adding devices
[   158.889] (==) Automatically enabling devices
[   158.889] (==) Automatically adding GPU devices
[   158.889] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   158.889]     Entry deleted from font path.
[   158.889] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   158.889]     Entry deleted from font path.
[   158.889] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   158.889]     Entry deleted from font path.
[   158.889] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   158.889]     Entry deleted from font path.
[   158.889] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   158.889]     Entry deleted from font path.
[   158.889] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[   158.889] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   158.889] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   158.889] (II) Loader magic: 0x7fd7740c2d80
[   158.889] (II) Module ABI versions:
[   158.889]     X.Org ANSI C Emulation: 0.4
[   158.889]     X.Org Video Driver: 18.0
[   158.889]     X.Org XInput driver : 21.0
[   158.889]     X.Org Server Extension : 8.0
[   158.889] (II) xfree86: Adding drm device (/dev/dri/card0)
[   158.891] (--) PCI:*(0:0:2:0) 8086:0166:1028:05b8 rev 9, Mem @ 0xc1000000/4194304, 0xb0000000/268435456, I/O @ 0x00004000/64
[   158.891] (--) PCI: (0:1:0:0) 1002:6601:1028:05b8 rev 0, Mem @ 0xa0000000/268435456, 0xc0000000/262144, I/O @ 0x00003000/256, BIOS @ 0x????????/131072
[   158.891] (II) LoadModule: "glx"
[   158.892] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/extensions/libglx.so
[   158.892] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[   158.892]     compiled for 6.9.0, module version = 1.0.0
[   158.892] (II) LoadModule: "fglrx"
[   158.892] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
[   158.922] (II) Module fglrx: vendor="FireGL - AMD Technologies Inc."
[   158.922]     compiled for 1.4.99.906, module version = 14.20.7
[   158.922]     Module class: X.Org Video Driver
[   158.922] (II) Loading sub module "fglrxdrm"
[   158.922] (II) LoadModule: "fglrxdrm"
[   158.922] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[   158.922] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[   158.922]     compiled for 1.4.99.906, module version = 14.20.7
[   158.922] (II) AMD Proprietary Linux Driver Version Identifier:14.20.7
[   158.922] (II) AMD Proprietary Linux Driver Release Identifier: UNSUPPORTED-14.201.1006.1002         
[   158.922] (II) AMD Proprietary Linux Driver Build Date: Sep  2 2014 10:14:55
[   158.922] (--) using VT number 8


[   159.008] (WW) Falling back to old probe method for fglrx
[   159.018] (II) Loading PCS database from /etc/ati/amdpcsdb /etc/ati/amdpcsdb.default
[   159.021] ukiDynamicMajor: found major device number 250
[   159.021] ukiDynamicMajor: found major device number 250
[   159.021] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[   159.021] ukiOpenDevice: node name is /dev/ati/card0
[   159.022] ukiOpenDevice: open result is 9, (OK)
[   159.022] ukiOpenByBusid: ukiOpenMinor returns 9
[   159.022] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[   159.094] (--) Chipset Supported AMD Graphics Processor (0x6601) found
[   159.094] (II) fglrx: intel VGA device detected, load intel driver.
[   159.094] (II) LoadModule: "intel"
[   159.094] (WW) Warning, couldn't open module intel
[   159.094] (II) UnloadModule: "intel"
[   159.094] (II) Unloading intel
[   159.094] (EE) Failed to load module "intel" (module does not exist, 0)
[   159.094] (WW) fglrx: Fail to load intel driver!
[   159.095] (II) fglrx(0): pEnt->device->identifier=0x7fd77416acf0
[   159.095] (II) fglrx(0): === [xdl_xs116_atiddxPreInit] === begin
[   159.095] (EE) 
[   159.095] (EE) Backtrace:
[   159.096] (EE) 0: /usr/bin/X (xorg_backtrace+0x56) [0x7fd773e3af76]
[   159.096] (EE) 1: /usr/bin/X (0x7fd773c84000+0x1bb179) [0x7fd773e3f179]
[   159.096] (EE) 2: /lib/x86_64-linux-gnu/libc.so.6 (0x7fd7719be000+0x36eb0) [0x7fd7719f4eb0]
[   159.096] (EE) 3: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so (xdl_xs116_atiddxPxPreInit+0xeb) [0x7fd76ed6588b]
[   159.096] (EE) 4: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so (xdl_xs116_atiddxPreInit+0x226b) [0x7fd76ed40d4b]
[   159.097] (EE) 5: /usr/bin/X (InitOutput+0xabb) [0x7fd773d1e3ab]
[   159.097] (EE) 6: /usr/bin/X (0x7fd773c84000+0x5b51a) [0x7fd773cdf51a]
[   159.097] (EE) 7: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xf5) [0x7fd7719dfec5]
[   159.097] (EE) 8: /usr/bin/X (0x7fd773c84000+0x45a8e) [0x7fd773cc9a8e]
[   159.097] (EE) 
[   159.097] (EE) Segmentation fault at address 0x38
[   159.097] (EE) 
Fatal server error:
[   159.097] (EE) Caught signal 11 (Segmentation fault). Server aborting
[   159.097] (EE) 
[   159.097] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[   159.097] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   159.097] (EE) 
[   159.223] (EE) Server terminated with error (1). Closing log file.



```

thank you in advance :)

---

