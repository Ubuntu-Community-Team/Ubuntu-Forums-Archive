---
title: "nvidia problems"
date: 2013-08-19
forum: General Help
---

### Post by netopalis45 on 2013-08-19
While changing my monitor setup I somehow managed to disable my nvidia video drivers. Now whenever I boot the computer it flashes the Ubuntu loading screen and then goes plank or distorts the screen and hangs. I have tried removing the drivers from the terminal and reinstalling them to no avail. I can't remeber what kind of nvidia card I have but I was previously using the experimental beta drivers. What else can I do?

---

### Post by papibe on 2013-08-19
Hi netopalis45.

Try this:

Go to text mode by pressing Ctrl+Alt+F1. Login and run this:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old

sudo nvidia-xconfig
```
Then restart your machine by running:
```
sudo reboot
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by netopalis45 on 2013-08-19
Unfortunately that did not work. I just removed all the nvidia drivers again to see what would happen. When it boots I get an error saying "kvm: disabled by bios" twice and that is all that is on the screen. When I remove all the nvidia drivers I have installed "sudo apt-get remove nvidia-* -y" and then use "sudo apt-get autoremove -y" and then reboot they all still seem to be there when I use "dpkg -l | grep nvidia" but they don't seem to be installed at all. I was under the impression that using those commands and rebooting would remove them completely.

---

### Post by papibe on 2013-08-19
Sorry to hear that.

Try removing the X config file and see if that lets you go into the nouveau driver:
```
sudo rm -rf /etc/X11/xorg.conf

sudo reboot
```
Regards.

---

### Post by netopalis45 on 2013-08-19
Still not working. I have purged all the nvidia drivers and reinstalled nvidia-current and nvidia-common and nvidia-settings added itself. What are the names of the other drivers that can be installed?

---

### Post by Yellow Pasque on 2013-08-19
/var/log/Xorg.0.log might be helpful

---

### Post by netopalis45 on 2013-08-19
This is what that log says

[     2.876] 
X.Org X Server 1.13.0
Release Date: 2012-09-05
[     2.876] X Protocol Version 11, Revision 0
[     2.876] Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu
[     2.876] Current Operating System: Linux joshscomputer 3.5.0-37-generic #58-Ubuntu SMP Mon Jul 8 22:07:55 UTC 2013 x86_64
[     2.876] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-37-generic root=UUID=282ffef8-cec4-488d-8e48-5104dd9bab39 ro quiet splash
[     2.876] Build Date: 11 April 2013  11:49:23PM
[     2.876] xorg-server 2:1.13.0-0ubuntu6.1~precise3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[     2.876] Current version of pixman: 0.26.0
[     2.876]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[     2.876] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     2.876] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Aug 18 21:41:34 2013
[     2.876] (==) Using config file: "/etc/X11/xorg.conf"
[     2.876] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     2.876] (==) ServerLayout "Layout0"
[     2.876] (**) |-->Screen "Screen0" (0)
[     2.876] (**) |   |-->Monitor "Monitor0"
[     2.876] (**) |   |-->Device "Device0"
[     2.876] (**) |-->Input Device "Keyboard0"
[     2.876] (**) |-->Input Device "Mouse0"
[     2.876] (**) Option "Xinerama" "0"
[     2.876] (==) Automatically adding devices
[     2.876] (==) Automatically enabling devices
[     2.876] (==) Automatically adding GPU devices
[     2.876] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     2.876]     Entry deleted from font path.
[     2.876] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     2.876]     Entry deleted from font path.
[     2.876] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     2.876]     Entry deleted from font path.
[     2.876] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     2.876]     Entry deleted from font path.
[     2.876] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     2.876]     Entry deleted from font path.
[     2.876] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[     2.876]     Entry deleted from font path.
[     2.876] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     2.876] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     2.876] (**) Extension "Composite" is disabled
[     2.876] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[     2.876] (WW) Disabling Keyboard0
[     2.876] (WW) Disabling Mouse0
[     2.876] (II) Loader magic: 0x7f2c7bc79c20
[     2.876] (II) Module ABI versions:
[     2.876]     X.Org ANSI C Emulation: 0.4
[     2.876]     X.Org Video Driver: 13.0
[     2.876]     X.Org XInput driver : 18.0
[     2.876]     X.Org Server Extension : 7.0
[     2.878] (--) PCI:*(0:1:0:0) 10de:104a:3842:2619 rev 161, Mem @ 0xf6000000/16777216, 0xe8000000/134217728, 0xf0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[     2.878] (II) Open ACPI successful (/var/run/acpid.socket)
[     2.878] Initializing built-in extension Generic Event Extension
[     2.878] Initializing built-in extension SHAPE
[     2.878] Initializing built-in extension MIT-SHM
[     2.878] Initializing built-in extension XInputExtension
[     2.878] Initializing built-in extension XTEST
[     2.878] Initializing built-in extension BIG-REQUESTS
[     2.878] Initializing built-in extension SYNC
[     2.879] Initializing built-in extension XKEYBOARD
[     2.879] Initializing built-in extension XC-MISC
[     2.879] Initializing built-in extension SECURITY
[     2.879] Initializing built-in extension XINERAMA
[     2.879] Initializing built-in extension XFIXES
[     2.879] Initializing built-in extension RENDER
[     2.879] Initializing built-in extension RANDR
[     2.879] Initializing built-in extension COMPOSITE
[     2.879] Initializing built-in extension DAMAGE
[     2.879] Initializing built-in extension MIT-SCREEN-SAVER
[     2.879] Initializing built-in extension DOUBLE-BUFFER
[     2.879] Initializing built-in extension RECORD
[     2.879] Initializing built-in extension DPMS
[     2.879] Initializing built-in extension X-Resource
[     2.879] Initializing built-in extension XVideo
[     2.879] Initializing built-in extension XVideo-MotionCompensation
[     2.879] Initializing built-in extension XFree86-VidModeExtension
[     2.879] Initializing built-in extension XFree86-DGA
[     2.879] Initializing built-in extension XFree86-DRI
[     2.879] Initializing built-in extension DRI2
[     2.879] (II) LoadModule: "glx"
[     2.879] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[     2.884] (II) Module glx: vendor="NVIDIA Corporation"
[     2.884]     compiled for 4.0.2, module version = 1.0.0
[     2.884]     Module class: X.Org Server Extension
[     2.884] (II) NVIDIA GLX Module  304.88  Wed Mar 27 14:46:57 PDT 2013
[     2.884] Loading extension GLX
[     2.884] (II) LoadModule: "nvidia"
[     2.884] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[     2.892] (II) Module nvidia: vendor="NVIDIA Corporation"
[     2.892]     compiled for 4.0.2, module version = 1.0.0
[     2.892]     Module class: X.Org Video Driver
[     2.892] (II) NVIDIA dlloader X Driver  304.88  Wed Mar 27 14:28:14 PDT 2013
[     2.892] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[     2.892] (++) using VT number 7

[     2.904] (II) Loading sub module "fb"
[     2.904] (II) LoadModule: "fb"
[     2.904] (II) Loading /usr/lib/xorg/modules/libfb.so
[     2.904] (II) Module fb: vendor="X.Org Foundation"
[     2.904]     compiled for 1.13.0, module version = 1.0.0
[     2.904]     ABI class: X.Org ANSI C Emulation, version 0.4
[     2.904] (II) Loading sub module "wfb"
[     2.904] (II) LoadModule: "wfb"
[     2.904] (II) Loading /usr/lib/xorg/modules/libwfb.so
[     2.904] (II) Module wfb: vendor="X.Org Foundation"
[     2.904]     compiled for 1.13.0, module version = 1.0.0
[     2.904]     ABI class: X.Org ANSI C Emulation, version 0.4
[     2.904] (II) Loading sub module "ramdac"
[     2.905] (II) LoadModule: "ramdac"
[     2.905] (II) Module "ramdac" already built-in
[     2.907] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[     2.907] (==) NVIDIA(0): RGB weight 888
[     2.907] (==) NVIDIA(0): Default visual is TrueColor
[     2.907] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[     2.907] (**) NVIDIA(0): Option "NoLogo" "True"
[     2.907] (**) NVIDIA(0): Option "Stereo" "0"
[     2.907] (**) NVIDIA(0): Option "nvidiaXineramaInfoOrder" "DFP-1"
[     2.907] (**) NVIDIA(0): Stereo disabled by request
[     2.907] (**) NVIDIA(0): Option "MetaModes" "DFP-0: nvidia-auto-select +1920+0, DFP-1: nvidia-auto-select +0+0; DFP-0: nvidia-auto-select +0+0"
[     2.907] (**) NVIDIA(0): Enabling 2D acceleration
[     3.708] (II) NVIDIA(GPU-0): Display (DELL 1800FP (DFP-0)) does not support NVIDIA 3D
[     3.708] (II) NVIDIA(GPU-0):     Vision stereo.
[     3.719] (II) NVIDIA(GPU-0): Display (Acer H233H (DFP-1)) does not support NVIDIA 3D Vision
[     3.719] (II) NVIDIA(GPU-0):     stereo.
[     3.720] (II) NVIDIA(0): NVIDIA GPU GeForce GT 610 (GF119) at PCI:1:0:0 (GPU-0)
[     3.720] (--) NVIDIA(0): Memory: 2097152 kBytes
[     3.720] (--) NVIDIA(0): VideoBIOS: 75.19.55.00.10
[     3.720] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[     3.720] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[     3.722] (--) NVIDIA(0): Valid display device(s) on GeForce GT 610 at PCI:1:0:0
[     3.722] (--) NVIDIA(0):     CRT-0
[     3.722] (--) NVIDIA(0):     CRT-1
[     3.722] (--) NVIDIA(0):     DELL 1800FP (DFP-0) (connected)
[     3.722] (--) NVIDIA(0):     Acer H233H (DFP-1) (connected)
[     3.722] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[     3.722] (--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
[     3.722] (--) NVIDIA(0): DELL 1800FP (DFP-0): 330.0 MHz maximum pixel clock
[     3.722] (--) NVIDIA(0): DELL 1800FP (DFP-0): Internal Dual Link TMDS
[     3.722] (--) NVIDIA(0): Acer H233H (DFP-1): 165.0 MHz maximum pixel clock
[     3.722] (--) NVIDIA(0): Acer H233H (DFP-1): Internal Single Link TMDS
[     3.722] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[     3.722] (**) NVIDIA(0):     device DELL 1800FP (DFP-0) (Using EDID frequencies has
[     3.722] (**) NVIDIA(0):     been enabled on all display devices.)
[     3.722] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[     3.722] (**) NVIDIA(0):     device Acer H233H (DFP-1) (Using EDID frequencies has been
[     3.722] (**) NVIDIA(0):     enabled on all display devices.)
[     3.723] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[     3.723] (WW) NVIDIA(GPU-0):     "720x480" is specified in the EDID; however, the EDID's
[     3.723] (WW) NVIDIA(GPU-0):     valid HorizSync range (31.000-83.000 kHz) would exclude
[     3.723] (WW) NVIDIA(GPU-0):     this mode's HorizSync (15.7 kHz); ignoring HorizSync check
[     3.723] (WW) NVIDIA(GPU-0):     for mode "720x480".
[     3.723] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[     3.723] (WW) NVIDIA(GPU-0):     "720x480" is specified in the EDID; however, the EDID's
[     3.723] (WW) NVIDIA(GPU-0):     valid HorizSync range (31.000-83.000 kHz) would exclude
[     3.723] (WW) NVIDIA(GPU-0):     this mode's HorizSync (15.7 kHz); ignoring HorizSync check
[     3.723] (WW) NVIDIA(GPU-0):     for mode "720x480".
[     3.723] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[     3.723] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[     3.723] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[     3.723] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[     3.723] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[     3.723] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[     3.723] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[     3.723] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[     3.723] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[     3.723] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[     3.723] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[     3.723] (WW) NVIDIA(GPU-0):     "1280x720" is specified in the EDID; however, the EDID's
[     3.723] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[     3.723] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[     3.723] (WW) NVIDIA(GPU-0):     check for mode "1280x720".
[     3.723] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[     3.723] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[     3.723] (WW) NVIDIA(GPU-0):     valid HorizSync range (31.000-83.000 kHz) would exclude
[     3.723] (WW) NVIDIA(GPU-0):     this mode's HorizSync (28.1 kHz); ignoring HorizSync check
[     3.723] (WW) NVIDIA(GPU-0):     for mode "1920x1080".
[     3.723] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[     3.723] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[     3.723] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[     3.723] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[     3.723] (WW) NVIDIA(GPU-0):     check for mode "1920x1080".
[     3.723] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[     3.723] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[     3.723] (WW) NVIDIA(GPU-0):     valid HorizSync range (31.000-83.000 kHz) would exclude
[     3.723] (WW) NVIDIA(GPU-0):     this mode's HorizSync (15.6 kHz); ignoring HorizSync check
[     3.723] (WW) NVIDIA(GPU-0):     for mode "720x576".
[     3.723] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[     3.723] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[     3.723] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[     3.723] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[     3.723] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[     3.723] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[     3.723] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[     3.723] (WW) NVIDIA(GPU-0):     valid HorizSync range (31.000-83.000 kHz) would exclude
[     3.723] (WW) NVIDIA(GPU-0):     this mode's HorizSync (15.6 kHz); ignoring HorizSync check
[     3.723] (WW) NVIDIA(GPU-0):     for mode "720x576".
[     3.723] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[     3.723] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[     3.723] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[     3.723] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[     3.723] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[     3.723] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[     3.723] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[     3.723] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[     3.723] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[     3.723] (WW) NVIDIA(GPU-0):     check for mode "1920x1080".
[     3.724] (II) NVIDIA(0): Validated MetaModes:
[     3.724] (II) NVIDIA(0):    
[     3.725] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select+1920+0,DFP-1:nvidia-auto-select+0+0"
[     3.725] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select+0+0"
[     3.725] (II) NVIDIA(0): Virtual screen size determined to be 3200 x 1080
[     3.754] (--) NVIDIA(0): DPI set to (90, 89); computed from "UseEdidDpi" X config
[     3.754] (--) NVIDIA(0):     option
[     3.754] (--) Depth 24 pixmap format is 32 bpp
[     3.754] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[     3.754] (II) NVIDIA:     access.
[     3.757] (II) NVIDIA(0): Setting mode "DFP-0:nvidia-auto-select+1920+0,DFP-1:nvidia-auto-select+0+0"
[     3.797] Loading extension NV-GLX
[     3.847] (==) NVIDIA(0): Disabling shared memory pixmaps
[     3.847] (==) NVIDIA(0): Backing store disabled
[     3.847] (==) NVIDIA(0): Silken mouse enabled
[     3.847] (**) NVIDIA(0): DPMS enabled
[     3.847] Loading extension NV-CONTROL
[     3.848] Loading extension XINERAMA
[     3.848] (II) Loading sub module "dri2"
[     3.848] (II) LoadModule: "dri2"
[     3.848] (II) Module "dri2" already built-in
[     3.848] (II) NVIDIA(0): [DRI2] Setup complete
[     3.848] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[     3.848] (--) RandR disabled
[     3.850] (II) Initializing extension GLX
[     3.857] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     3.858] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     3.858] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     3.858] (II) LoadModule: "evdev"
[     3.858] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     3.858] (II) Module evdev: vendor="X.Org Foundation"
[     3.858]     compiled for 1.13.0, module version = 2.7.3
[     3.858]     Module class: X.Org XInput Driver
[     3.858]     ABI class: X.Org XInput driver, version 18.0
[     3.858] (II) Using input driver 'evdev' for 'Power Button'
[     3.859] (**) Power Button: always reports core events
[     3.859] (**) evdev: Power Button: Device: "/dev/input/event1"
[     3.859] (--) evdev: Power Button: Vendor 0 Product 0x1
[     3.859] (--) evdev: Power Button: Found keys
[     3.859] (II) evdev: Power Button: Configuring as keyboard
[     3.859] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[     3.859] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     3.859] (**) Option "xkb_rules" "evdev"
[     3.859] (**) Option "xkb_model" "pc105"
[     3.859] (**) Option "xkb_layout" "us"
[     3.859] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     3.859] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     3.859] (II) Using input driver 'evdev' for 'Power Button'
[     3.859] (**) Power Button: always reports core events
[     3.859] (**) evdev: Power Button: Device: "/dev/input/event0"
[     3.859] (--) evdev: Power Button: Vendor 0 Product 0x1
[     3.859] (--) evdev: Power Button: Found keys
[     3.859] (II) evdev: Power Button: Configuring as keyboard
[     3.859] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[     3.859] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[     3.859] (**) Option "xkb_rules" "evdev"
[     3.859] (**) Option "xkb_model" "pc105"
[     3.859] (**) Option "xkb_layout" "us"
[     3.859] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event13)
[     3.859] (II) No input driver specified, ignoring this device.
[     3.859] (II) This device may have been added with another device file.
[     3.859] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event14)
[     3.859] (II) No input driver specified, ignoring this device.
[     3.859] (II) This device may have been added with another device file.
[     3.859] (II) config/udev: Adding input device HDA Intel PCH Line Out Front (/dev/input/event10)
[     3.859] (II) No input driver specified, ignoring this device.
[     3.859] (II) This device may have been added with another device file.
[     3.859] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event3)
[     3.859] (II) No input driver specified, ignoring this device.
[     3.859] (II) This device may have been added with another device file.
[     3.860] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event4)
[     3.860] (II) No input driver specified, ignoring this device.
[     3.860] (II) This device may have been added with another device file.
[     3.860] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event5)
[     3.860] (II) No input driver specified, ignoring this device.
[     3.860] (II) This device may have been added with another device file.
[     3.860] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event6)
[     3.860] (II) No input driver specified, ignoring this device.
[     3.860] (II) This device may have been added with another device file.
[     3.860] (II) config/udev: Adding input device HDA Intel PCH Line Out Side (/dev/input/event7)
[     3.860] (II) No input driver specified, ignoring this device.
[     3.860] (II) This device may have been added with another device file.
[     3.860] (II) config/udev: Adding input device HDA Intel PCH Line Out CLFE (/dev/input/event8)
[     3.860] (II) No input driver specified, ignoring this device.
[     3.860] (II) This device may have been added with another device file.
[     3.860] (II) config/udev: Adding input device HDA Intel PCH Line Out Surround (/dev/input/event9)
[     3.860] (II) No input driver specified, ignoring this device.
[     3.860] (II) This device may have been added with another device file.
[     3.860] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:1025 (/dev/input/event11)
[     3.860] (**) Logitech Unifying Device. Wireless PID:1025: Applying InputClass "evdev pointer catchall"
[     3.860] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:1025'
[     3.860] (**) Logitech Unifying Device. Wireless PID:1025: always reports core events
[     3.860] (**) evdev: Logitech Unifying Device. Wireless PID:1025: Device: "/dev/input/event11"
[     3.860] (--) evdev: Logitech Unifying Device. Wireless PID:1025: Vendor 0x46d Product 0xc52b
[     3.860] (--) evdev: Logitech Unifying Device. Wireless PID:1025: Found 20 mouse buttons
[     3.860] (--) evdev: Logitech Unifying Device. Wireless PID:1025: Found scroll wheel(s)
[     3.860] (--) evdev: Logitech Unifying Device. Wireless PID:1025: Found relative axes
[     3.860] (--) evdev: Logitech Unifying Device. Wireless PID:1025: Found x and y relative axes
[     3.860] (II) evdev: Logitech Unifying Device. Wireless PID:1025: Configuring as mouse
[     3.860] (II) evdev: Logitech Unifying Device. Wireless PID:1025: Adding scrollwheel support
[     3.860] (**) evdev: Logitech Unifying Device. Wireless PID:1025: YAxisMapping: buttons 4 and 5
[     3.860] (**) evdev: Logitech Unifying Device. Wireless PID:1025: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     3.860] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2/0003:046D:C52B.0004/input/input11/event11"
[     3.860] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:1025" (type: MOUSE, id 8)
[     3.860] (II) evdev: Logitech Unifying Device. Wireless PID:1025: initialized for relative axes.
[     3.860] (**) Logitech Unifying Device. Wireless PID:1025: (accel) keeping acceleration scheme 1
[     3.860] (**) Logitech Unifying Device. Wireless PID:1025: (accel) acceleration profile 0
[     3.860] (**) Logitech Unifying Device. Wireless PID:1025: (accel) acceleration factor: 2.000
[     3.860] (**) Logitech Unifying Device. Wireless PID:1025: (accel) acceleration threshold: 4
[     3.861] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:1025 (/dev/input/mouse0)
[     3.861] (II) No input driver specified, ignoring this device.
[     3.861] (II) This device may have been added with another device file.
[     3.861] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:200a (/dev/input/event12)
[     3.861] (**) Logitech Unifying Device. Wireless PID:200a: Applying InputClass "evdev keyboard catchall"
[     3.861] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:200a'
[     3.861] (**) Logitech Unifying Device. Wireless PID:200a: always reports core events
[     3.861] (**) evdev: Logitech Unifying Device. Wireless PID:200a: Device: "/dev/input/event12"
[     3.861] (--) evdev: Logitech Unifying Device. Wireless PID:200a: Vendor 0x46d Product 0xc52b
[     3.861] (--) evdev: Logitech Unifying Device. Wireless PID:200a: Found 1 mouse buttons
[     3.861] (--) evdev: Logitech Unifying Device. Wireless PID:200a: Found scroll wheel(s)
[     3.861] (--) evdev: Logitech Unifying Device. Wireless PID:200a: Found relative axes
[     3.861] (II) evdev: Logitech Unifying Device. Wireless PID:200a: Forcing relative x/y axes to exist.
[     3.861] (--) evdev: Logitech Unifying Device. Wireless PID:200a: Found absolute axes
[     3.861] (II) evdev: Logitech Unifying Device. Wireless PID:200a: Forcing absolute x/y axes to exist.
[     3.861] (--) evdev: Logitech Unifying Device. Wireless PID:200a: Found keys
[     3.861] (II) evdev: Logitech Unifying Device. Wireless PID:200a: Configuring as mouse
[     3.861] (II) evdev: Logitech Unifying Device. Wireless PID:200a: Configuring as keyboard
[     3.861] (II) evdev: Logitech Unifying Device. Wireless PID:200a: Adding scrollwheel support
[     3.861] (**) evdev: Logitech Unifying Device. Wireless PID:200a: YAxisMapping: buttons 4 and 5
[     3.861] (**) evdev: Logitech Unifying Device. Wireless PID:200a: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     3.861] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2/0003:046D:C52B.0004/input/input12/event12"
[     3.861] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:200a" (type: KEYBOARD, id 9)
[     3.861] (**) Option "xkb_rules" "evdev"
[     3.861] (**) Option "xkb_model" "pc105"
[     3.861] (**) Option "xkb_layout" "us"
[     3.861] (II) evdev: Logitech Unifying Device. Wireless PID:200a: initialized for relative axes.
[     3.861] (WW) evdev: Logitech Unifying Device. Wireless PID:200a: ignoring absolute axes.
[     3.861] (**) Logitech Unifying Device. Wireless PID:200a: (accel) keeping acceleration scheme 1
[     3.861] (**) Logitech Unifying Device. Wireless PID:200a: (accel) acceleration profile 0
[     3.861] (**) Logitech Unifying Device. Wireless PID:200a: (accel) acceleration factor: 2.000
[     3.861] (**) Logitech Unifying Device. Wireless PID:200a: (accel) acceleration threshold: 4
[     3.861] (II) config/udev: Adding input device Eee PC WMI hotkeys (/dev/input/event2)
[     3.861] (**) Eee PC WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[     3.861] (II) Using input driver 'evdev' for 'Eee PC WMI hotkeys'
[     3.861] (**) Eee PC WMI hotkeys: always reports core events
[     3.861] (**) evdev: Eee PC WMI hotkeys: Device: "/dev/input/event2"
[     3.861] (--) evdev: Eee PC WMI hotkeys: Vendor 0 Product 0
[     3.861] (--) evdev: Eee PC WMI hotkeys: Found keys
[     3.861] (II) evdev: Eee PC WMI hotkeys: Configuring as keyboard
[     3.861] (**) Option "config_info" "udev:/sys/devices/platform/eeepc-wmi/input/input2/event2"
[     3.861] (II) XINPUT: Adding extended input device "Eee PC WMI hotkeys" (type: KEYBOARD, id 10)
[     3.861] (**) Option "xkb_rules" "evdev"
[     3.861] (**) Option "xkb_model" "pc105"
[     3.861] (**) Option "xkb_layout" "us"
[     3.987] (II) NVIDIA(GPU-0): Display (DELL 1800FP (DFP-0)) does not support NVIDIA 3D
[     3.987] (II) NVIDIA(GPU-0):     Vision stereo.
[     3.987] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[     3.987] (**) NVIDIA(0):     device DELL 1800FP (DFP-0) (Using EDID frequencies has
[     3.987] (**) NVIDIA(0):     been enabled on all display devices.)
[     3.998] (II) NVIDIA(GPU-0): Display (Acer H233H (DFP-1)) does not support NVIDIA 3D Vision
[     3.998] (II) NVIDIA(GPU-0):     stereo.
[     3.998] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[     3.998] (**) NVIDIA(0):     device Acer H233H (DFP-1) (Using EDID frequencies has been
[     3.998] (**) NVIDIA(0):     enabled on all display devices.)
[     3.998] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[     3.998] (WW) NVIDIA(GPU-0):     "720x480" is specified in the EDID; however, the EDID's
[     3.998] (WW) NVIDIA(GPU-0):     valid HorizSync range (31.000-83.000 kHz) would exclude
[     3.998] (WW) NVIDIA(GPU-0):     this mode's HorizSync (15.7 kHz); ignoring HorizSync check
[     3.998] (WW) NVIDIA(GPU-0):     for mode "720x480".
[     3.998] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[     3.998] (WW) NVIDIA(GPU-0):     "720x480" is specified in the EDID; however, the EDID's
[     3.999] (WW) NVIDIA(GPU-0):     valid HorizSync range (31.000-83.000 kHz) would exclude
[     3.999] (WW) NVIDIA(GPU-0):     this mode's HorizSync (15.7 kHz); ignoring HorizSync check
[     3.999] (WW) NVIDIA(GPU-0):     for mode "720x480".
[     3.999] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[     3.999] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[     3.999] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[     3.999] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[     3.999] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[     3.999] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[     3.999] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[     3.999] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[     3.999] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[     3.999] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[     3.999] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[     3.999] (WW) NVIDIA(GPU-0):     "1280x720" is specified in the EDID; however, the EDID's
[     3.999] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[     3.999] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[     3.999] (WW) NVIDIA(GPU-0):     check for mode "1280x720".
[     3.999] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[     3.999] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[     3.999] (WW) NVIDIA(GPU-0):     valid HorizSync range (31.000-83.000 kHz) would exclude
[     3.999] (WW) NVIDIA(GPU-0):     this mode's HorizSync (28.1 kHz); ignoring HorizSync check
[     3.999] (WW) NVIDIA(GPU-0):     for mode "1920x1080".
[     3.999] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[     3.999] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[     3.999] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[     3.999] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[     3.999] (WW) NVIDIA(GPU-0):     check for mode "1920x1080".
[     3.999] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[     3.999] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[     3.999] (WW) NVIDIA(GPU-0):     valid HorizSync range (31.000-83.000 kHz) would exclude
[     3.999] (WW) NVIDIA(GPU-0):     this mode's HorizSync (15.6 kHz); ignoring HorizSync check
[     3.999] (WW) NVIDIA(GPU-0):     for mode "720x576".
[     3.999] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[     3.999] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[     3.999] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[     3.999] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[     3.999] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[     3.999] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[     3.999] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[     3.999] (WW) NVIDIA(GPU-0):     valid HorizSync range (31.000-83.000 kHz) would exclude
[     3.999] (WW) NVIDIA(GPU-0):     this mode's HorizSync (15.6 kHz); ignoring HorizSync check
[     3.999] (WW) NVIDIA(GPU-0):     for mode "720x576".
[     3.999] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[     3.999] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[     3.999] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[     3.999] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[     3.999] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[     3.999] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[     3.999] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[     3.999] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[     3.999] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[     3.999] (WW) NVIDIA(GPU-0):     check for mode "1920x1080".
[     4.297] (II) NVIDIA(GPU-0): Display (DELL 1800FP (DFP-0)) does not support NVIDIA 3D
[     4.297] (II) NVIDIA(GPU-0):     Vision stereo.
[     4.297] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[     4.297] (**) NVIDIA(0):     device DELL 1800FP (DFP-0) (Using EDID frequencies has
[     4.297] (**) NVIDIA(0):     been enabled on all display devices.)
[     4.308] (II) NVIDIA(GPU-0): Display (Acer H233H (DFP-1)) does not support NVIDIA 3D Vision
[     4.308] (II) NVIDIA(GPU-0):     stereo.
[     4.308] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[     4.308] (**) NVIDIA(0):     device Acer H233H (DFP-1) (Using EDID frequencies has been
[     4.308] (**) NVIDIA(0):     enabled on all display devices.)
[     4.309] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[     4.309] (WW) NVIDIA(GPU-0):     "720x480" is specified in the EDID; however, the EDID's
[     4.309] (WW) NVIDIA(GPU-0):     valid HorizSync range (31.000-83.000 kHz) would exclude
[     4.309] (WW) NVIDIA(GPU-0):     this mode's HorizSync (15.7 kHz); ignoring HorizSync check
[     4.309] (WW) NVIDIA(GPU-0):     for mode "720x480".
[     4.309] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[     4.309] (WW) NVIDIA(GPU-0):     "720x480" is specified in the EDID; however, the EDID's
[     4.309] (WW) NVIDIA(GPU-0):     valid HorizSync range (31.000-83.000 kHz) would exclude
[     4.309] (WW) NVIDIA(GPU-0):     this mode's HorizSync (15.7 kHz); ignoring HorizSync check
[     4.309] (WW) NVIDIA(GPU-0):     for mode "720x480".
[     4.309] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[     4.309] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[     4.309] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[     4.309] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[     4.309] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[     4.309] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[     4.309] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[     4.309] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[     4.309] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[     4.309] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[     4.309] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[     4.309] (WW) NVIDIA(GPU-0):     "1280x720" is specified in the EDID; however, the EDID's
[     4.309] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[     4.309] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[     4.309] (WW) NVIDIA(GPU-0):     check for mode "1280x720".
[     4.309] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[     4.309] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[     4.309] (WW) NVIDIA(GPU-0):     valid HorizSync range (31.000-83.000 kHz) would exclude
[     4.309] (WW) NVIDIA(GPU-0):     this mode's HorizSync (28.1 kHz); ignoring HorizSync check
[     4.309] (WW) NVIDIA(GPU-0):     for mode "1920x1080".
[     4.309] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[     4.309] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[     4.309] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[     4.309] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[     4.309] (WW) NVIDIA(GPU-0):     check for mode "1920x1080".
[     4.309] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[     4.309] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[     4.309] (WW) NVIDIA(GPU-0):     valid HorizSync range (31.000-83.000 kHz) would exclude
[     4.309] (WW) NVIDIA(GPU-0):     this mode's HorizSync (15.6 kHz); ignoring HorizSync check
[     4.309] (WW) NVIDIA(GPU-0):     for mode "720x576".
[     4.309] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[     4.309] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[     4.309] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[     4.309] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[     4.309] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[     4.309] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[     4.309] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[     4.309] (WW) NVIDIA(GPU-0):     valid HorizSync range (31.000-83.000 kHz) would exclude
[     4.309] (WW) NVIDIA(GPU-0):     this mode's HorizSync (15.6 kHz); ignoring HorizSync check
[     4.309] (WW) NVIDIA(GPU-0):     for mode "720x576".
[     4.309] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[     4.309] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[     4.309] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[     4.309] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[     4.309] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[     4.309] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[     4.309] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[     4.309] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[     4.309] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[     4.309] (WW) NVIDIA(GPU-0):     check for mode "1920x1080".
[    24.308] (II) NVIDIA(GPU-0): Display (DELL 1800FP (DFP-0)) does not support NVIDIA 3D
[    24.308] (II) NVIDIA(GPU-0):     Vision stereo.
[    24.308] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    24.308] (**) NVIDIA(0):     device DELL 1800FP (DFP-0) (Using EDID frequencies has
[    24.308] (**) NVIDIA(0):     been enabled on all display devices.)
[    24.319] (II) NVIDIA(GPU-0): Display (Acer H233H (DFP-1)) does not support NVIDIA 3D Vision
[    24.319] (II) NVIDIA(GPU-0):     stereo.
[    24.319] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    24.319] (**) NVIDIA(0):     device Acer H233H (DFP-1) (Using EDID frequencies has been
[    24.319] (**) NVIDIA(0):     enabled on all display devices.)
[    24.320] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    24.320] (WW) NVIDIA(GPU-0):     "720x480" is specified in the EDID; however, the EDID's
[    24.320] (WW) NVIDIA(GPU-0):     valid HorizSync range (31.000-83.000 kHz) would exclude
[    24.320] (WW) NVIDIA(GPU-0):     this mode's HorizSync (15.7 kHz); ignoring HorizSync check
[    24.320] (WW) NVIDIA(GPU-0):     for mode "720x480".
[    24.320] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    24.320] (WW) NVIDIA(GPU-0):     "720x480" is specified in the EDID; however, the EDID's
[    24.320] (WW) NVIDIA(GPU-0):     valid HorizSync range (31.000-83.000 kHz) would exclude
[    24.320] (WW) NVIDIA(GPU-0):     this mode's HorizSync (15.7 kHz); ignoring HorizSync check
[    24.320] (WW) NVIDIA(GPU-0):     for mode "720x480".
[    24.320] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    24.320] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    24.320] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[    24.320] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    24.320] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    24.320] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    24.320] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    24.320] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[    24.320] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    24.320] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    24.320] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    24.320] (WW) NVIDIA(GPU-0):     "1280x720" is specified in the EDID; however, the EDID's
[    24.320] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[    24.320] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    24.320] (WW) NVIDIA(GPU-0):     check for mode "1280x720".
[    24.320] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    24.320] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    24.320] (WW) NVIDIA(GPU-0):     valid HorizSync range (31.000-83.000 kHz) would exclude
[    24.320] (WW) NVIDIA(GPU-0):     this mode's HorizSync (28.1 kHz); ignoring HorizSync check
[    24.320] (WW) NVIDIA(GPU-0):     for mode "1920x1080".
[    24.320] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    24.320] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    24.320] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[    24.320] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    24.320] (WW) NVIDIA(GPU-0):     check for mode "1920x1080".
[    24.320] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    24.320] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    24.320] (WW) NVIDIA(GPU-0):     valid HorizSync range (31.000-83.000 kHz) would exclude
[    24.320] (WW) NVIDIA(GPU-0):     this mode's HorizSync (15.6 kHz); ignoring HorizSync check
[    24.320] (WW) NVIDIA(GPU-0):     for mode "720x576".
[    24.320] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    24.320] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    24.320] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[    24.320] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    24.320] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    24.321] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    24.321] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    24.321] (WW) NVIDIA(GPU-0):     valid HorizSync range (31.000-83.000 kHz) would exclude
[    24.321] (WW) NVIDIA(GPU-0):     this mode's HorizSync (15.6 kHz); ignoring HorizSync check
[    24.321] (WW) NVIDIA(GPU-0):     for mode "720x576".
[    24.321] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    24.321] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    24.321] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[    24.321] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    24.321] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    24.321] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    24.321] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    24.321] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[    24.321] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    24.321] (WW) NVIDIA(GPU-0):     check for mode "1920x1080".
[    24.555] (II) NVIDIA(0): Setting mode "DVI-I-1: nvidia-auto-select @1280x1024 +1920+56"
[    24.623] (II) NVIDIA(0): Setting mode "DVI-I-1: nvidia-auto-select @1280x1024 +1920+56, HDMI-0: nvidia-auto-select @1920x1080 +0+0"
[    24.739] (II) NVIDIA(GPU-0): Display (DELL 1800FP (DFP-0)) does not support NVIDIA 3D
[    24.739] (II) NVIDIA(GPU-0):     Vision stereo.
[    24.739] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    24.739] (**) NVIDIA(0):     device DELL 1800FP (DFP-0) (Using EDID frequencies has
[    24.739] (**) NVIDIA(0):     been enabled on all display devices.)
[    24.750] (II) NVIDIA(GPU-0): Display (Acer H233H (DFP-1)) does not support NVIDIA 3D Vision
[    24.750] (II) NVIDIA(GPU-0):     stereo.
[    24.750] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    24.750] (**) NVIDIA(0):     device Acer H233H (DFP-1) (Using EDID frequencies has been
[    24.750] (**) NVIDIA(0):     enabled on all display devices.)
[    24.750] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    24.750] (WW) NVIDIA(GPU-0):     "720x480" is specified in the EDID; however, the EDID's
[    24.750] (WW) NVIDIA(GPU-0):     valid HorizSync range (31.000-83.000 kHz) would exclude
[    24.750] (WW) NVIDIA(GPU-0):     this mode's HorizSync (15.7 kHz); ignoring HorizSync check
[    24.750] (WW) NVIDIA(GPU-0):     for mode "720x480".
[    24.751] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    24.751] (WW) NVIDIA(GPU-0):     "720x480" is specified in the EDID; however, the EDID's
[    24.751] (WW) NVIDIA(GPU-0):     valid HorizSync range (31.000-83.000 kHz) would exclude
[    24.751] (WW) NVIDIA(GPU-0):     this mode's HorizSync (15.7 kHz); ignoring HorizSync check
[    24.751] (WW) NVIDIA(GPU-0):     for mode "720x480".
[    24.751] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    24.751] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    24.751] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[    24.751] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    24.751] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    24.751] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    24.751] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    24.751] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[    24.751] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    24.751] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    24.751] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    24.751] (WW) NVIDIA(GPU-0):     "1280x720" is specified in the EDID; however, the EDID's
[    24.751] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[    24.751] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    24.751] (WW) NVIDIA(GPU-0):     check for mode "1280x720".
[    24.751] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    24.751] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    24.751] (WW) NVIDIA(GPU-0):     valid HorizSync range (31.000-83.000 kHz) would exclude
[    24.751] (WW) NVIDIA(GPU-0):     this mode's HorizSync (28.1 kHz); ignoring HorizSync check
[    24.751] (WW) NVIDIA(GPU-0):     for mode "1920x1080".
[    24.751] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    24.751] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    24.751] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[    24.751] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    24.751] (WW) NVIDIA(GPU-0):     check for mode "1920x1080".
[    24.751] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    24.751] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    24.751] (WW) NVIDIA(GPU-0):     valid HorizSync range (31.000-83.000 kHz) would exclude
[    24.751] (WW) NVIDIA(GPU-0):     this mode's HorizSync (15.6 kHz); ignoring HorizSync check
[    24.751] (WW) NVIDIA(GPU-0):     for mode "720x576".
[    24.751] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    24.751] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    24.751] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[    24.751] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    24.751] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    24.751] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    24.751] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    24.751] (WW) NVIDIA(GPU-0):     valid HorizSync range (31.000-83.000 kHz) would exclude
[    24.751] (WW) NVIDIA(GPU-0):     this mode's HorizSync (15.6 kHz); ignoring HorizSync check
[    24.751] (WW) NVIDIA(GPU-0):     for mode "720x576".
[    24.751] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    24.751] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    24.751] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[    24.751] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    24.751] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    24.751] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    24.751] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    24.751] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[    24.751] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    24.751] (WW) NVIDIA(GPU-0):     check for mode "1920x1080".
[    24.775] (II) XKB: reuse xkmfile /var/lib/xkb/server-8C3648A5FD728529D869F46730BE1BC287DB231C.xkm
[    25.013] (II) NVIDIA(GPU-0): Display (DELL 1800FP (DFP-0)) does not support NVIDIA 3D
[    25.013] (II) NVIDIA(GPU-0):     Vision stereo.
[    25.013] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    25.013] (**) NVIDIA(0):     device DELL 1800FP (DFP-0) (Using EDID frequencies has
[    25.013] (**) NVIDIA(0):     been enabled on all display devices.)
[    25.024] (II) NVIDIA(GPU-0): Display (Acer H233H (DFP-1)) does not support NVIDIA 3D Vision
[    25.024] (II) NVIDIA(GPU-0):     stereo.
[    25.024] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    25.024] (**) NVIDIA(0):     device Acer H233H (DFP-1) (Using EDID frequencies has been
[    25.024] (**) NVIDIA(0):     enabled on all display devices.)
[    25.025] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    25.025] (WW) NVIDIA(GPU-0):     "720x480" is specified in the EDID; however, the EDID's
[    25.025] (WW) NVIDIA(GPU-0):     valid HorizSync range (31.000-83.000 kHz) would exclude
[    25.025] (WW) NVIDIA(GPU-0):     this mode's HorizSync (15.7 kHz); ignoring HorizSync check
[    25.025] (WW) NVIDIA(GPU-0):     for mode "720x480".
[    25.025] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    25.025] (WW) NVIDIA(GPU-0):     "720x480" is specified in the EDID; however, the EDID's
[    25.025] (WW) NVIDIA(GPU-0):     valid HorizSync range (31.000-83.000 kHz) would exclude
[    25.025] (WW) NVIDIA(GPU-0):     this mode's HorizSync (15.7 kHz); ignoring HorizSync check
[    25.025] (WW) NVIDIA(GPU-0):     for mode "720x480".
[    25.025] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    25.025] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    25.025] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[    25.025] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    25.025] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    25.025] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    25.025] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    25.025] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[    25.025] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    25.025] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    25.025] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    25.025] (WW) NVIDIA(GPU-0):     "1280x720" is specified in the EDID; however, the EDID's
[    25.025] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[    25.025] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    25.025] (WW) NVIDIA(GPU-0):     check for mode "1280x720".
[    25.025] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    25.025] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    25.025] (WW) NVIDIA(GPU-0):     valid HorizSync range (31.000-83.000 kHz) would exclude
[    25.025] (WW) NVIDIA(GPU-0):     this mode's HorizSync (28.1 kHz); ignoring HorizSync check
[    25.025] (WW) NVIDIA(GPU-0):     for mode "1920x1080".
[    25.025] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    25.025] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    25.025] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[    25.025] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    25.025] (WW) NVIDIA(GPU-0):     check for mode "1920x1080".
[    25.025] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    25.025] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    25.025] (WW) NVIDIA(GPU-0):     valid HorizSync range (31.000-83.000 kHz) would exclude
[    25.025] (WW) NVIDIA(GPU-0):     this mode's HorizSync (15.6 kHz); ignoring HorizSync check
[    25.025] (WW) NVIDIA(GPU-0):     for mode "720x576".
[    25.025] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    25.025] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    25.025] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[    25.025] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    25.025] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    25.025] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    25.025] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    25.025] (WW) NVIDIA(GPU-0):     valid HorizSync range (31.000-83.000 kHz) would exclude
[    25.025] (WW) NVIDIA(GPU-0):     this mode's HorizSync (15.6 kHz); ignoring HorizSync check
[    25.025] (WW) NVIDIA(GPU-0):     for mode "720x576".
[    25.025] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    25.025] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    25.025] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[    25.025] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    25.025] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    25.025] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    25.025] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    25.025] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[    25.025] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    25.025] (WW) NVIDIA(GPU-0):     check for mode "1920x1080".
[    25.045] (II) NVIDIA(GPU-0): Display (DELL 1800FP (DFP-0)) does not support NVIDIA 3D
[    25.045] (II) NVIDIA(GPU-0):     Vision stereo.
[    25.046] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    25.046] (**) NVIDIA(0):     device DELL 1800FP (DFP-0) (Using EDID frequencies has
[    25.046] (**) NVIDIA(0):     been enabled on all display devices.)
[    25.057] (II) NVIDIA(GPU-0): Display (Acer H233H (DFP-1)) does not support NVIDIA 3D Vision
[    25.057] (II) NVIDIA(GPU-0):     stereo.
[    25.057] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    25.057] (**) NVIDIA(0):     device Acer H233H (DFP-1) (Using EDID frequencies has been
[    25.057] (**) NVIDIA(0):     enabled on all display devices.)
[    25.057] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    25.057] (WW) NVIDIA(GPU-0):     "720x480" is specified in the EDID; however, the EDID's
[    25.057] (WW) NVIDIA(GPU-0):     valid HorizSync range (31.000-83.000 kHz) would exclude
[    25.057] (WW) NVIDIA(GPU-0):     this mode's HorizSync (15.7 kHz); ignoring HorizSync check
[    25.057] (WW) NVIDIA(GPU-0):     for mode "720x480".
[    25.057] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    25.057] (WW) NVIDIA(GPU-0):     "720x480" is specified in the EDID; however, the EDID's
[    25.057] (WW) NVIDIA(GPU-0):     valid HorizSync range (31.000-83.000 kHz) would exclude
[    25.057] (WW) NVIDIA(GPU-0):     this mode's HorizSync (15.7 kHz); ignoring HorizSync check
[    25.057] (WW) NVIDIA(GPU-0):     for mode "720x480".
[    25.057] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    25.057] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    25.057] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[    25.057] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    25.057] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    25.057] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    25.057] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    25.057] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[    25.057] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    25.057] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    25.058] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    25.058] (WW) NVIDIA(GPU-0):     "1280x720" is specified in the EDID; however, the EDID's
[    25.058] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[    25.058] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    25.058] (WW) NVIDIA(GPU-0):     check for mode "1280x720".
[    25.058] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    25.058] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    25.058] (WW) NVIDIA(GPU-0):     valid HorizSync range (31.000-83.000 kHz) would exclude
[    25.058] (WW) NVIDIA(GPU-0):     this mode's HorizSync (28.1 kHz); ignoring HorizSync check
[    25.058] (WW) NVIDIA(GPU-0):     for mode "1920x1080".
[    25.058] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    25.058] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    25.058] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[    25.058] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    25.058] (WW) NVIDIA(GPU-0):     check for mode "1920x1080".
[    25.058] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    25.058] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    25.058] (WW) NVIDIA(GPU-0):     valid HorizSync range (31.000-83.000 kHz) would exclude
[    25.058] (WW) NVIDIA(GPU-0):     this mode's HorizSync (15.6 kHz); ignoring HorizSync check
[    25.058] (WW) NVIDIA(GPU-0):     for mode "720x576".
[    25.058] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    25.058] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    25.058] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[    25.058] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    25.058] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    25.058] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    25.058] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    25.058] (WW) NVIDIA(GPU-0):     valid HorizSync range (31.000-83.000 kHz) would exclude
[    25.058] (WW) NVIDIA(GPU-0):     this mode's HorizSync (15.6 kHz); ignoring HorizSync check
[    25.058] (WW) NVIDIA(GPU-0):     for mode "720x576".
[    25.058] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    25.058] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    25.058] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[    25.058] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    25.058] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    25.058] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    25.058] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    25.058] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[    25.058] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    25.058] (WW) NVIDIA(GPU-0):     check for mode "1920x1080".
[    86.559] (II) NVIDIA(GPU-0): Display (DELL 1800FP (DFP-0)) does not support NVIDIA 3D
[    86.559] (II) NVIDIA(GPU-0):     Vision stereo.
[    86.559] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    86.559] (**) NVIDIA(0):     device DELL 1800FP (DFP-0) (Using EDID frequencies has
[    86.559] (**) NVIDIA(0):     been enabled on all display devices.)
[    86.571] (II) NVIDIA(GPU-0): Display (Acer H233H (DFP-1)) does not support NVIDIA 3D Vision
[    86.571] (II) NVIDIA(GPU-0):     stereo.
[    86.571] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    86.571] (**) NVIDIA(0):     device Acer H233H (DFP-1) (Using EDID frequencies has been
[    86.571] (**) NVIDIA(0):     enabled on all display devices.)
[    86.571] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    86.571] (WW) NVIDIA(GPU-0):     "720x480" is specified in the EDID; however, the EDID's
[    86.571] (WW) NVIDIA(GPU-0):     valid HorizSync range (31.000-83.000 kHz) would exclude
[    86.571] (WW) NVIDIA(GPU-0):     this mode's HorizSync (15.7 kHz); ignoring HorizSync check
[    86.571] (WW) NVIDIA(GPU-0):     for mode "720x480".
[    86.571] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    86.571] (WW) NVIDIA(GPU-0):     "720x480" is specified in the EDID; however, the EDID's
[    86.571] (WW) NVIDIA(GPU-0):     valid HorizSync range (31.000-83.000 kHz) would exclude
[    86.571] (WW) NVIDIA(GPU-0):     this mode's HorizSync (15.7 kHz); ignoring HorizSync check
[    86.571] (WW) NVIDIA(GPU-0):     for mode "720x480".
[    86.571] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    86.571] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    86.571] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[    86.571] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    86.571] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    86.571] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    86.571] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    86.571] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[    86.571] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    86.571] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    86.571] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    86.571] (WW) NVIDIA(GPU-0):     "1280x720" is specified in the EDID; however, the EDID's
[    86.571] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[    86.571] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    86.571] (WW) NVIDIA(GPU-0):     check for mode "1280x720".
[    86.571] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    86.571] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    86.571] (WW) NVIDIA(GPU-0):     valid HorizSync range (31.000-83.000 kHz) would exclude
[    86.571] (WW) NVIDIA(GPU-0):     this mode's HorizSync (28.1 kHz); ignoring HorizSync check
[    86.572] (WW) NVIDIA(GPU-0):     for mode "1920x1080".
[    86.572] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    86.572] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    86.572] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[    86.572] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    86.572] (WW) NVIDIA(GPU-0):     check for mode "1920x1080".
[    86.572] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    86.572] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    86.572] (WW) NVIDIA(GPU-0):     valid HorizSync range (31.000-83.000 kHz) would exclude
[    86.572] (WW) NVIDIA(GPU-0):     this mode's HorizSync (15.6 kHz); ignoring HorizSync check
[    86.572] (WW) NVIDIA(GPU-0):     for mode "720x576".
[    86.572] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    86.572] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    86.572] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[    86.572] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    86.572] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    86.572] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    86.572] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    86.572] (WW) NVIDIA(GPU-0):     valid HorizSync range (31.000-83.000 kHz) would exclude
[    86.572] (WW) NVIDIA(GPU-0):     this mode's HorizSync (15.6 kHz); ignoring HorizSync check
[    86.572] (WW) NVIDIA(GPU-0):     for mode "720x576".
[    86.572] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    86.572] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    86.572] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[    86.572] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    86.572] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    86.572] (WW) NVIDIA(GPU-0): The EDID for Acer H233H (DFP-1) contradicts itself: mode
[    86.572] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    86.572] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-76.000 Hz) would exclude
[    86.572] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    86.572] (WW) NVIDIA(GPU-0):     check for mode "1920x1080".
[   359.187] (II) evdev: Eee PC WMI hotkeys: Close
[   359.187] (II) UnloadModule: "evdev"
[   359.187] (II) evdev: Logitech Unifying Device. Wireless PID:200a: Close
[   359.187] (II) UnloadModule: "evdev"
[   359.187] (II) evdev: Logitech Unifying Device. Wireless PID:1025: Close
[   359.187] (II) UnloadModule: "evdev"
[   359.187] (II) evdev: Power Button: Close
[   359.187] (II) UnloadModule: "evdev"
[   359.187] (II) evdev: Power Button: Close
[   359.187] (II) UnloadModule: "evdev"
[   359.386] Server terminated successfully (0). Closing log file.

---

