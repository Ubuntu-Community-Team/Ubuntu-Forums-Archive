---
title: "Slow boot time and login"
date: 2013-10-09
forum: General Help
---

### Post by mindbox on 2013-10-09
I have ubuntu 12.04 installed on dual boot with windows 8. I installed xfce, kde, gnome, and cinnamon. My broblem is is takes at least two minutes to boot and login. I've read other posts on this topic and have looked at logs and bootchart but I don't know what to do. I'm posting my logs so someone can hopefully know how to help me with all the things that go wrong. I'm a novice when it comes to linux. 

**lscpu reaveals **
```

Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                4
On-line CPU(s) list:   0-3
Thread(s) per core:    2
Core(s) per socket:    2
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 58
Stepping:              9
CPU MHz:               1200.000
BogoMIPS:              5786.68
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              4096K
NUMA node0 CPU(s):     0-3
```

Boot Chart image is attached 


**dgm greeter log **

```

=== xinerama setup Configuration ===
  Clone: false
  Output: Laptop attached to LVDS1
     status: on
     width: 1600
     height: 900
     rate: 60
     primary: true
     position: 0 0
  Output: (null) attached to VGA1
     status: off
     width: -1
     height: -1
     rate: -1
     primary: false
     position: -1 -1
  Output: (null) attached to HDMI1
     status: off
     width: -1
     height: -1
     rate: -1
     primary: false
     position: -1 -1
  Output: (null) attached to DP1
     status: off
     width: -1
     height: -1
     rate: -1
     primary: false
     position: -1 -1
=== Applying Configuration Configuration ===
  Clone: false
  Output: Laptop attached to LVDS1
     status: on
     width: 1600
     height: 900
     rate: 60
     primary: true
     position: 0 0
  Output: (null) attached to VGA1
     status: off
     width: -1
     height: -1
     rate: -1
     primary: false
     position: -1 -1
  Output: (null) attached to HDMI1
     status: off
     width: -1
     height: -1
     rate: -1
     primary: false
     position: -1 -1
  Output: (null) attached to DP1
     status: off
     width: -1
     height: -1
     rate: -1
     primary: false
     position: -1 -1
gnome-session[2247]: WARNING: Failed to start app: Unable to start application: Failed to execute child process "gnome-power-manager" (No such file or directory)
gdm-simple-greeter[2768]: Gtk-WARNING: Overriding tab label for notebook
gdm-simple-greeter[2768]: Gtk-WARNING: Overriding tab label for notebook
gdm-simple-greeter[2768]: Gtk-WARNING: Overriding tab label for notebook
gdm-simple-greeter[2768]: Gtk-WARNING: Overriding tab label for notebook
gdm-simple-greeter[2768]: Gtk-WARNING: Overriding tab label for notebook
gdm-simple-greeter[2768]: Gtk-WARNING: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkwidget.c:7117: widget not within a GtkWindow
gdm-simple-greeter[2768]: Gtk-CRITICAL: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed
gdm-simple-greeter[2768]: Gtk-CRITICAL: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed
gdm-simple-greeter[2768]: Gtk-WARNING: gtk_widget_size_allocate(): attempt to allocate widget with width -47 and height -47
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1200007 (Login Wind)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
gdm-simple-greeter[2768]: Gtk-CRITICAL: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed
gdm-simple-greeter[2768]: Gtk-CRITICAL: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed
gdm-simple-greeter[2768]: Gtk-WARNING: gtk_widget_size_allocate(): attempt to allocate widget with width -47 and height -47
gdm-simple-greeter[2768]: CRITICAL: get_column_number: assertion `i < gtk_tree_view_get_n_columns (treeview)' failed
gdm-simple-greeter[2768]: CRITICAL: get_column_number: assertion `i < gtk_tree_view_get_n_columns (treeview)' failed

(gnome-settings-daemon:2262): color-plugin-WARNING **: failed to create directory on startup: Error creating directory: Permission denied

(gnome-settings-daemon:2262): color-plugin-WARNING **: failed to create profile from EDID data: Error creating directory: Permission denied
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1200007 (Login Wind)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus the no_focus_window with a timestamp of 0.  This shouldn't happen!
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.

** (gnome-settings-daemon:2262): WARNING **: Name taken or bus went away - shutting down

(gnome-settings-daemon:2262): libappindicator-WARNING **: Unable to send signal for NewStatus: The connection is closed


```

**gdm slave log **
```


gdm-simple-slave[1698]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
gdm-simple-slave[1698]: CRITICAL: gdm_session_direct_get_username: assertion `session != NULL' failed
gdm-session-worker[2814]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
gdm-session-worker[2814]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
gdm-session-worker[2814]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "dan"
gdm-session-worker[3617]: pam_ecryptfs: Passphrase file wrapped
gdm-session-worker[2814]: AccountsService-WARNING: SetLanguage call failed: running '/usr/share/language-tools/set-language-helper' failed: no output
gdm-session-worker[2814]: pam_unix(gdm:session): session opened for user dan by (uid=0)
gdm-session-worker[2814]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0

```

**gdm 0 log**
```


X.Org X Server 1.13.0
Release Date: 2012-09-05
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu
Current Operating System: Linux dansmachine 3.5.0-41-generic #64~precise1-Ubuntu SMP Thu Sep 12 16:50:04 UTC 2013 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-41-generic root=UUID=9f591eb2-46bb-4fa6-ad80-497d0f08606c ro quiet, splash vt.handoff=7
Build Date: 11 April 2013  11:49:23PM
xorg-server 2:1.13.0-0ubuntu6.1~precise3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.24.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Oct  9 18:14:44 2013
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(==) Automatically adding GPU devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
    Entry deleted from font path.
(WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    built-ins
(==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) config/udev: Adding drm device (/dev/dri/card0)
(--) PCI:*(0:0:2:0) 8086:0166:17aa:3977 rev 9, Mem @ 0xe0000000/4194304, 0xd0000000/268435456, I/O @ 0x00003000/64
Initializing built-in extension Generic Event Extension
Initializing built-in extension SHAPE
Initializing built-in extension MIT-SHM
Initializing built-in extension XInputExtension
Initializing built-in extension XTEST
Initializing built-in extension BIG-REQUESTS
Initializing built-in extension SYNC
Initializing built-in extension XKEYBOARD
Initializing built-in extension XC-MISC
Initializing built-in extension SECURITY
Initializing built-in extension XINERAMA
Initializing built-in extension XFIXES
Initializing built-in extension RENDER
Initializing built-in extension RANDR
Initializing built-in extension COMPOSITE
Initializing built-in extension DAMAGE
Initializing built-in extension MIT-SCREEN-SAVER
Initializing built-in extension DOUBLE-BUFFER
Initializing built-in extension RECORD
Initializing built-in extension DPMS
Initializing built-in extension X-Resource
Initializing built-in extension XVideo
Initializing built-in extension XVideo-MotionCompensation
Initializing built-in extension XFree86-VidModeExtension
Initializing built-in extension XFree86-DGA
Initializing built-in extension XFree86-DRI
Initializing built-in extension DRI2
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.13.0, module version = 1.0.0
(==) AIGLX enabled
Loading extension GLX
(==) Matched intel as autoconfigured driver 0
(==) Matched intel as autoconfigured driver 1
(==) Matched vesa as autoconfigured driver 2
(==) Matched modesetting as autoconfigured driver 3
(==) Matched fbdev as autoconfigured driver 4
(==) Assigned the driver to the xf86ConfigLayout
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
    compiled for 1.13.0, module version = 2.20.9
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
    compiled for 1.13.0, module version = 2.3.2
(II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
(II) Module modesetting: vendor="X.Org Foundation"
    compiled for 1.13.0, module version = 0.5.0
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
    compiled for 1.13.0, module version = 0.4.3
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
    Ivybridge Server (GT2), HD Graphics, HD Graphics 4600,
    Haswell Desktop (GT3), HD Graphics, HD Graphics 4600,
    Haswell Mobile (GT3), HD Graphics, HD Graphics P4600/P4700,
    Haswell Server (GT3), Haswell (GT1), Haswell (GT2), Haswell (GT3),
    HD Graphics, Haswell (GT2), Haswell (GT3), Haswell SDV Desktop (GT1),
    Haswell SDV Desktop (GT2), Haswell SDV Desktop (GT3),
    Haswell SDV Mobile (GT1), Haswell SDV Mobile (GT2),
    Haswell SDV Mobile (GT3), Haswell SDV Server (GT1),
    Haswell SDV Server (GT2), Haswell SDV Server (GT3),
    Haswell SDV (GT1), Haswell SDV (GT2), Haswell SDV (GT3),
    Haswell SDV (GT1), Haswell SDV (GT2), Haswell SDV (GT3),
    Haswell ULT Desktop (GT1), Haswell ULT Desktop (GT2),
    Iris(TM) Graphics 5100, HD Graphics, HD Graphics 4400,
    HD Graphics 5000, Haswell ULT Server (GT1), Haswell ULT Server (GT2),
    Iris(TM) Graphics 5100, Haswell ULT (GT1), Haswell ULT (GT2),
    Iris(TM) Graphics 5100, HD Graphics, HD Graphics 4200,
    Iris(TM) Graphics 5100, Haswell CRW Desktop (GT1), HD Graphics 4600,
    Iris(TM) Pro Graphics 5200, Haswell CRW Mobile (GT1),
    HD Graphics 4600, Iris(TM) Pro Graphics 5200,
    Haswell CRW Server (GT1), Haswell CRW Server (GT2),
    Iris(TM) Pro Graphics 5200, Haswell CRW (GT1), Haswell CRW (GT2),
    Iris(TM) Pro Graphics 5200, Haswell CRW (GT1), Haswell CRW (GT2),
    Iris(TM) Pro Graphics 5200, ValleyView PO board
(II) VESA: driver for VESA chipsets: vesa
(II) modesetting: Driver for Modesetting Kernel Drivers: kms
(II) FBDEV: driver for framebuffer: fbdev
(++) using VT number 7

(II) intel(0): using device path '/dev/dri/card0'
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for modesetting
(WW) Falling back to old probe method for fbdev
(II) Loading /usr/lib/xorg/modules/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.13.0, module version = 0.0.2
(II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(--) intel(0): Integrated Graphics Chipset: Intel(R) Ivybridge Mobile (GT2)
(**) intel(0): Relaxed fencing enabled
(**) intel(0): Wait on SwapBuffers? enabled
(**) intel(0): Triple buffering? enabled
(**) intel(0): Framebuffer tiled
(**) intel(0): Pixmaps tiled
(**) intel(0): 3D buffers tiled
(**) intel(0): SwapBuffers wait enabled
(==) intel(0): video overlay key set to 0x101fe
(II) intel(0): Output LVDS1 has no monitor section
(--) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
(II) intel(0): Output VGA1 has no monitor section
(II) intel(0): Output HDMI1 has no monitor section
(II) intel(0): Output DP1 has no monitor section
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: CMN  Model: 1728  Serial#: 0
(II) intel(0): Year: 2011  Week: 50
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 39  vert.: 22
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.613 redY: 0.344   greenX: 0.326 greenY: 0.590
(II) intel(0): blueX: 0.160 blueY: 0.082   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 107.8 MHz   Image Size:  382 x 215 mm
(II) intel(0): h_active: 1600  h_sync: 1648  h_sync_end 1680 h_blank_end 1940 h_border: 0
(II) intel(0): v_active: 900  v_sync: 903  v_sync_end 908 v_blanking: 926 v_border: 0
(II) intel(0):  N173FGE-L23
(II) intel(0):  CMN
(II) intel(0):  N173FGE-L23
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff000dae281700000000
(II) intel(0):     32150103802716780a08059d58539729
(II) intel(0):     15505400000001010101010101010101
(II) intel(0):     0101010101011c2a405461841a303020
(II) intel(0):     35007ed71000001a000000fe004e3137
(II) intel(0):     334647452d4c32332020000000fe0043
(II) intel(0):     4d4e0a202020202020202020000000fe
(II) intel(0):     004e3137334647452d4c3233202000e3
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
(II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
(II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
(II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1600x900"x60.0  107.80  1600 1648 1680 1940  900 903 908 926 +hsync -vsync (55.6 kHz eP)
(II) intel(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz d)
(II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz d)
(II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz d)
(II) intel(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz d)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz d)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output HDMI1
(II) intel(0): EDID for output DP1
(II) intel(0): Output LVDS1 connected
(II) intel(0): Output VGA1 disconnected
(II) intel(0): Output HDMI1 disconnected
(II) intel(0): Output DP1 disconnected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output LVDS1 using initial mode 1600x900
(II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(II) intel(0): Kernel page flipping support detected, enabling
(==) intel(0): DPI set to (96, 96)
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.13.0, module version = 1.0.0
(II) Unloading vesa
(II) Unloading modesetting
(II) Unloading fbdev
(II) Unloading fbdevhw
(==) Depth 24 pixmap format is 32 bpp
(II) intel(0): [DRI2] Setup complete
(II) intel(0): [DRI2]   DRI driver: i965
(II) intel(0): Allocated new frame buffer 1600x900 stride 6656, tiled
(II) UXA(0): Driver registered support for the following operations:
(II)         solid
(II)         copy
(II)         composite (RENDER acceleration)
(II)         put_image
(II)         get_image
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(==) intel(0): DPMS enabled
(==) intel(0): Intel XvMC decoder enabled
(II) intel(0): Set up textured video
(II) intel(0): [XvMC] xvmc_vld driver initialized.
(II) intel(0): direct rendering: DRI2 Enabled
(==) intel(0): hotplug detection: "enabled"
(--) RandR disabled
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_INTEL_swap_event
(II) AIGLX: enabled GLX_ARB_create_context
(II) AIGLX: enabled GLX_ARB_create_context_profile
(II) AIGLX: enabled GLX_EXT_create_context_es2_profile
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
(II) AIGLX: Loaded and initialized i965
(II) GLX: Initialized DRI2 GL provider for screen 0
(II) intel(0): Setting screen physical size to 423 x 238
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event3)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.13.0, module version = 2.7.3
(II) Using input driver 'evdev' for 'Power Button'
(**) Power Button: always reports core events
(**) evdev: Power Button: Device: "/dev/input/event3"
(--) evdev: Power Button: Vendor 0 Product 0x1
(--) evdev: Power Button: Found keys
(II) evdev: Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
(II) config/udev: Adding input device Video Bus (/dev/input/event5)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(II) Using input driver 'evdev' for 'Video Bus'
(**) Video Bus: always reports core events
(**) evdev: Video Bus: Device: "/dev/input/event5"
(--) evdev: Video Bus: Vendor 0 Product 0x6
(--) evdev: Video Bus: Found keys
(II) evdev: Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) Using input driver 'evdev' for 'Power Button'
(**) Power Button: always reports core events
(**) evdev: Power Button: Device: "/dev/input/event0"
(--) evdev: Power Button: Vendor 0 Product 0x1
(--) evdev: Power Button: Found keys
(II) evdev: Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
(II) config/udev: Adding input device Sleep Button (/dev/input/event1)
(**) Sleep Button: Applying InputClass "evdev keyboard catchall"
(II) Using input driver 'evdev' for 'Sleep Button'
(**) Sleep Button: always reports core events
(**) evdev: Sleep Button: Device: "/dev/input/event1"
(--) evdev: Sleep Button: Vendor 0 Product 0x3
(--) evdev: Sleep Button: Found keys
(II) evdev: Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
(II) config/udev: Adding input device Lid Switch (/dev/input/event2)
(II) No input driver specified, ignoring this device.
(II) This device may have been added with another device file.
(II) config/udev: Adding drm device (/dev/dri/card0)
(II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event10)
(II) No input driver specified, ignoring this device.
(II) This device may have been added with another device file.
(II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event11)
(II) No input driver specified, ignoring this device.
(II) This device may have been added with another device file.
(II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event9)
(II) No input driver specified, ignoring this device.
(II) This device may have been added with another device file.
(II) config/udev: Adding input device Lenovo EasyCamera (/dev/input/event7)
(**) Lenovo EasyCamera: Applying InputClass "evdev keyboard catchall"
(II) Using input driver 'evdev' for 'Lenovo EasyCamera'
(**) Lenovo EasyCamera: always reports core events
(**) evdev: Lenovo EasyCamera: Device: "/dev/input/event7"
(--) evdev: Lenovo EasyCamera: Vendor 0x4f2 Product 0xb2e1
(--) evdev: Lenovo EasyCamera: Found keys
(II) evdev: Lenovo EasyCamera: Configuring as keyboard
(II) XINPUT: Adding extended input device "Lenovo EasyCamera" (type: KEYBOARD, id 10)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
(**) AT Translated Set 2 keyboard: always reports core events
(**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
(--) evdev: AT Translated Set 2 keyboard: Found keys
(II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event8)
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
    compiled for 1.13.0, module version = 1.6.2
(II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) synaptics: SynPS/2 Synaptics TouchPad: ignoring touch events for semi-multitouch device
(--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5728
(--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4902
(--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
(--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
(--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
(--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 12)
(**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
(**) synaptics: SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
(**) synaptics: SynPS/2 Synaptics TouchPad: AccelFactor is now 0.036
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
(--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
(**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
(II) config/udev: Adding input device Ideapad extra buttons (/dev/input/event6)
(**) Ideapad extra buttons: Applying InputClass "evdev keyboard catchall"
(II) Using input driver 'evdev' for 'Ideapad extra buttons'
(**) Ideapad extra buttons: always reports core events
(**) evdev: Ideapad extra buttons: Device: "/dev/input/event6"
(--) evdev: Ideapad extra buttons: Vendor 0 Product 0
(--) evdev: Ideapad extra buttons: Found keys
(II) evdev: Ideapad extra buttons: Configuring as keyboard
(II) XINPUT: Adding extended input device "Ideapad extra buttons" (type: KEYBOARD, id 13)
(II) intel(0): EDID vendor "CMN", prod id 5928
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0  107.80  1600 1648 1680 1940  900 903 908 926 +hsync -vsync (55.6 kHz eP)
(II) intel(0): EDID vendor "CMN", prod id 5928
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0  107.80  1600 1648 1680 1940  900 903 908 926 +hsync -vsync (55.6 kHz eP)
(II) intel(0): EDID vendor "CMN", prod id 5928
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0  107.80  1600 1648 1680 1940  900 903 908 926 +hsync -vsync (55.6 kHz eP)
(II) intel(0): EDID vendor "CMN", prod id 5928
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0  107.80  1600 1648 1680 1940  900 903 908 926 +hsync -vsync (55.6 kHz eP)
(II) intel(0): EDID vendor "CMN", prod id 5928
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0  107.80  1600 1648 1680 1940  900 903 908 926 +hsync -vsync (55.6 kHz eP)
(II) intel(0): EDID vendor "CMN", prod id 5928
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0  107.80  1600 1648 1680 1940  900 903 908 926 +hsync -vsync (55.6 kHz eP)
(II) intel(0): EDID vendor "CMN", prod id 5928
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0  107.80  1600 1648 1680 1940  900 903 908 926 +hsync -vsync (55.6 kHz eP)
(II) intel(0): EDID vendor "CMN", prod id 5928
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0  107.80  1600 1648 1680 1940  900 903 908 926 +hsync -vsync (55.6 kHz eP)
(II) intel(0): EDID vendor "CMN", prod id 5928
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0  107.80  1600 1648 1680 1940  900 903 908 926 +hsync -vsync (55.6 kHz eP)
(II) intel(0): EDID vendor "CMN", prod id 5928
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0  107.80  1600 1648 1680 1940  900 903 908 926 +hsync -vsync (55.6 kHz eP)
(II) intel(0): EDID vendor "CMN", prod id 5928
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0  107.80  1600 1648 1680 1940  900 903 908 926 +hsync -vsync (55.6 kHz eP)
(II) intel(0): EDID vendor "CMN", prod id 5928
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0  107.80  1600 1648 1680 1940  900 903 908 926 +hsync -vsync (55.6 kHz eP)
(II) intel(0): EDID vendor "CMN", prod id 5928
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0  107.80  1600 1648 1680 1940  900 903 908 926 +hsync -vsync (55.6 kHz eP)
(II) intel(0): EDID vendor "CMN", prod id 5928
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0  107.80  1600 1648 1680 1940  900 903 908 926 +hsync -vsync (55.6 kHz eP)
(II) intel(0): EDID vendor "CMN", prod id 5928
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0  107.80  1600 1648 1680 1940  900 903 908 926 +hsync -vsync (55.6 kHz eP)
(II) intel(0): EDID vendor "CMN", prod id 5928
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0  107.80  1600 1648 1680 1940  900 903 908 926 +hsync -vsync (55.6 kHz eP)
(II) intel(0): EDID vendor "CMN", prod id 5928
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0  107.80  1600 1648 1680 1940  900 903 908 926 +hsync -vsync (55.6 kHz eP)
(II) intel(0): EDID vendor "CMN", prod id 5928
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0  107.80  1600 1648 1680 1940  900 903 908 926 +hsync -vsync (55.6 kHz eP)
(II) intel(0): EDID vendor "CMN", prod id 5928
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0  107.80  1600 1648 1680 1940  900 903 908 926 +hsync -vsync (55.6 kHz eP)
(II) intel(0): EDID vendor "CMN", prod id 5928
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0  107.80  1600 1648 1680 1940  900 903 908 926 +hsync -vsync (55.6 kHz eP)
(II) intel(0): EDID vendor "CMN", prod id 5928
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0  107.80  1600 1648 1680 1940  900 903 908 926 +hsync -vsync (55.6 kHz eP)
```

---

### Post by mindbox on 2013-10-18
I've tried reinstalling kdm, gdm, and lightdm and still have problems. I also deleted ~/.Xauthority. When I use lightdm it looks exacly like kdm. It doesn't have the nice look that it had when I first installed ubuntu

---

