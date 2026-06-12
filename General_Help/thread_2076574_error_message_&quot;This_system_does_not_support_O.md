---
title: "error message &quot;This system does not support OpenGL&quot;"
date: 2012-10-26
forum: General Help
---

### Post by r144 on 2012-10-26
hello fellow forum members,

since a month or so, I am running ubuntu natty on a virtualbox. Today I decided to try out freecad. But I am stuck with the message
*This system does not support OpenGL*

I have done some research. But none of the proposed solutions did work. This is what I find in /*var/log/Xorg.0.log*

```
[    84.993] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    84.994] X Protocol Version 11, Revision 0
[    84.994] Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
[    84.994] Current Operating System: Linux janus-ubuntu 2.6.38-16-generic #67-Ubuntu SMP Thu Sep 6 18:00:43 UTC 2012 i686
[    84.994] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-16-generic root=UUID=f7a14d43-f960-457a-b5b3-b1709fac238b ro splash quiet vt.handoff=7
[    84.994] Build Date: 13 October 2011  05:38:22PM
[    84.995] xorg-server 2:1.10.1-1ubuntu1.3 (For technical support please see http://www.ubuntu.com/support) 
[    84.995] Current version of pixman: 0.20.2
[    84.995]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    84.995] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    84.999] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Oct 26 14:33:45 2012
[    85.001] (==) Using config file: "/etc/X11/xorg.conf"
[    85.002] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    85.022] (==) No Layout section.  Using the first Screen section.
[    85.022] (**) |-->Screen "Default Screen" (0)
[    85.022] (**) |   |-->Monitor "Configured Monitor"
[    85.023] (==) No device specified for screen "Default Screen".
    Using the first device section listed.
[    85.023] (**) |   |-->Device "Configured Video Device"
[    85.023] (==) Automatically adding devices
[    85.023] (==) Automatically enabling devices
[    85.023] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    85.023]     Entry deleted from font path.
[    85.023] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    85.023]     Entry deleted from font path.
[    85.023] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    85.023]     Entry deleted from font path.
[    85.023] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    85.023]     Entry deleted from font path.
[    85.023] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    85.023]     Entry deleted from font path.
[    85.049] (WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
[    85.049]     Entry deleted from font path.
[    85.049]     (Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
[    85.049] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    85.049] (**) ModulePath set to "/usr/lib/nvidia-96/xorg,/usr/lib/xorg/modules"
[    85.049] (==) |-->Input Device "Configured Mouse"
[    85.049] (==) No Layout section. Using the first core pointer device.
[    85.049] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    85.049] (II) Loader magic: 0x8200ac0
[    85.049] (II) Module ABI versions:
[    85.049]     X.Org ANSI C Emulation: 0.4
[    85.049]     X.Org Video Driver: 10.0
[    85.049]     X.Org XInput driver : 12.3
[    85.049]     X.Org Server Extension : 5.0
[    85.051] (--) PCI:*(0:0:2:0) 80ee:beef:0000:0000 rev 0, Mem @ 0xe0000000/33554432
[    85.053] (II) Open ACPI successful (/var/run/acpid.socket)
[    85.053] (II) LoadModule: "extmod"
[    85.053] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    85.054] (II) Module extmod: vendor="X.Org Foundation"
[    85.054]     compiled for 1.10.1, module version = 1.0.0
[    85.054]     Module class: X.Org Server Extension
[    85.054]     ABI class: X.Org Server Extension, version 5.0
[    85.054] (II) Loading extension MIT-SCREEN-SAVER
[    85.054] (II) Loading extension XFree86-VidModeExtension
[    85.054] (II) Loading extension XFree86-DGA
[    85.054] (II) Loading extension DPMS
[    85.054] (II) Loading extension XVideo
[    85.054] (II) Loading extension XVideo-MotionCompensation
[    85.054] (II) Loading extension X-Resource
[    85.054] (II) LoadModule: "dbe"
[    85.054] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    85.054] (II) Module dbe: vendor="X.Org Foundation"
[    85.054]     compiled for 1.10.1, module version = 1.0.0
[    85.054]     Module class: X.Org Server Extension
[    85.054]     ABI class: X.Org Server Extension, version 5.0
[    85.054] (II) Loading extension DOUBLE-BUFFER
[    85.054] (II) LoadModule: "glx"
[    85.055] (II) Loading /usr/lib/nvidia-96/xorg/libglx.so
[    85.098] (II) Module glx: vendor="NVIDIA Corporation"
[    85.098]     compiled for 4.0.2, module version = 1.0.0
[    85.098]     Module class: X.Org Server Extension
[    85.098] (II) NVIDIA GLX Module  96.43.20  Sun Jul 17 23:48:16 PDT 2011
[    85.098] (II) Loading extension GLX
[    85.098] (II) LoadModule: "record"
[    85.098] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    85.098] (II) Module record: vendor="X.Org Foundation"
[    85.098]     compiled for 1.10.1, module version = 1.13.0
[    85.098]     Module class: X.Org Server Extension
[    85.098]     ABI class: X.Org Server Extension, version 5.0
[    85.098] (II) Loading extension RECORD
[    85.098] (II) LoadModule: "dri"
[    85.099] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    85.099] (II) Module dri: vendor="X.Org Foundation"
[    85.099]     compiled for 1.10.1, module version = 1.0.0
[    85.099]     ABI class: X.Org Server Extension, version 5.0
[    85.099] (II) Loading extension XFree86-DRI
[    85.099] (II) LoadModule: "dri2"
[    85.100] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    85.100] (II) Module dri2: vendor="X.Org Foundation"
[    85.100]     compiled for 1.10.1, module version = 1.2.0
[    85.100]     ABI class: X.Org Server Extension, version 5.0
[    85.100] (II) Loading extension DRI2
[    85.100] (==) Matched vboxvideo as autoconfigured driver 0
[    85.100] (==) Matched vesa as autoconfigured driver 1
[    85.100] (==) Matched fbdev as autoconfigured driver 2
[    85.100] (==) Assigned the driver to the xf86ConfigLayout
[    85.100] (II) LoadModule: "vboxvideo"
[    85.100] (II) Loading /usr/lib/xorg/modules/drivers/vboxvideo_drv.so
[    85.101] (II) Module vboxvideo: vendor="Oracle Corporation"
[    85.101]     compiled for 1.10.1, module version = 1.0.1
[    85.101]     Module class: X.Org Video Driver
[    85.101]     ABI class: X.Org Video Driver, version 10.0
[    85.101] (**) Load address of symbol "VBOXVIDEO" is 0x8853c0
[    85.101] (II) LoadModule: "vesa"
[    85.101] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    85.102] (II) Module vesa: vendor="X.Org Foundation"
[    85.102]     compiled for 1.10.0, module version = 2.3.0
[    85.102]     Module class: X.Org Video Driver
[    85.102]     ABI class: X.Org Video Driver, version 10.0
[    85.102] (II) LoadModule: "fbdev"
[    85.102] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    85.104] (II) Module fbdev: vendor="X.Org Foundation"
[    85.104]     compiled for 1.10.0, module version = 0.4.2
[    85.104]     ABI class: X.Org Video Driver, version 10.0
[    85.104] (II) LoadModule: "vboxmouse"
[    85.104] (II) Loading /usr/lib/xorg/modules/input/vboxmouse_drv.so
[    85.105] (II) Module vboxmouse: vendor="Oracle Corporation"
[    85.105]     compiled for 0.0.0, module version = 1.0.0
[    85.105]     Module class: X.Org XInput Driver
[    85.105]     ABI class: X.Org XInput driver, version 12.3
[    85.105] (**) Load address of symbol "VBOXMOUSE" is 0xe271c0
[    85.105] (II) VBoxVideo: guest driver for VirtualBox: vbox
[    85.105] (II) VESA: driver for VESA chipsets: vesa
[    85.105] (II) FBDEV: driver for framebuffer: fbdev
[    85.105] (--) using VT number 7

[    85.108] (II) Loading /usr/lib/xorg/modules/drivers/vboxvideo_drv.so
[    85.108] (WW) Falling back to old probe method for vesa
[    85.108] (WW) Falling back to old probe method for fbdev
[    85.108] (II) Loading sub module "fbdevhw"
[    85.108] (II) LoadModule: "fbdevhw"
[    85.115] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    85.115] (II) Module fbdevhw: vendor="X.Org Foundation"
[    85.115]     compiled for 1.10.1, module version = 0.0.2
[    85.115]     ABI class: X.Org Video Driver, version 10.0
[    85.115] (II) VBoxVideo(0): VirtualBox guest additions video driver version 4.0.4_OSE
[    85.117] (II) Loading sub module "ramdac"
[    85.117] (II) LoadModule: "ramdac"
[    85.117] (II) Module "ramdac" already built-in
[    85.117] (II) Loading sub module "vbe"
[    85.117] (II) LoadModule: "vbe"
[    85.117] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    85.117] (II) Module vbe: vendor="X.Org Foundation"
[    85.117]     compiled for 1.10.1, module version = 1.1.0
[    85.117]     ABI class: X.Org Video Driver, version 10.0
[    85.117] (II) Loading sub module "fb"
[    85.117] (II) LoadModule: "fb"
[    85.118] (II) Loading /usr/lib/xorg/modules/libfb.so
[    85.118] (II) Module fb: vendor="X.Org Foundation"
[    85.118]     compiled for 1.10.1, module version = 1.0.0
[    85.118]     ABI class: X.Org ANSI C Emulation, version 0.4
[    85.118] (II) Loading sub module "shadowfb"
[    85.118] (II) LoadModule: "shadowfb"
[    85.118] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[    85.118] (II) Module shadowfb: vendor="X.Org Foundation"
[    85.118]     compiled for 1.10.1, module version = 1.0.0
[    85.118]     ABI class: X.Org ANSI C Emulation, version 0.4
[    85.118] (II) Loading sub module "vgahw"
[    85.118] (II) LoadModule: "vgahw"
[    85.119] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    85.119] (II) Module vgahw: vendor="X.Org Foundation"
[    85.119]     compiled for 1.10.1, module version = 0.1.0
[    85.119]     ABI class: X.Org Video Driver, version 10.0
[    85.119] (II) Loading sub module "dri"
[    85.119] (II) LoadModule: "dri"
[    85.119] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    85.119] (II) Module dri: vendor="X.Org Foundation"
[    85.119]     compiled for 1.10.1, module version = 1.0.0
[    85.119]     ABI class: X.Org Server Extension, version 5.0
[    85.123] (==) VBoxVideo(0): Depth 24, (--) framebuffer bpp 32
[    85.124] (--) VBoxVideo(0): Virtual size is 32000x32000 (pitch 32000)
[    85.124] (**) VBoxVideo(0):  Built-in mode "VBoxInitialMode": 66.1 MHz (scaled from 0.0 MHz), 57.2 kHz, 60.0 Hz
[    85.124] (II) VBoxVideo(0): Modeline "VBoxInitialMode"x0.0   66.10  1150 1152 1154 1156  947 949 951 953 (57.2 kHz)
[    85.124] (**) VBoxVideo(0):  Built-in mode "VBoxDynamicMode": 66.1 MHz (scaled from 0.0 MHz), 57.2 kHz, 60.0 Hz
[    85.124] (II) VBoxVideo(0): Modeline "VBoxDynamicMode"x0.0   66.10  1150 1152 1154 1156  947 949 951 953 (57.2 kHz)
[    85.124] (**) VBoxVideo(0):  Built-in mode "VBoxDynamicMode": 66.1 MHz (scaled from 0.0 MHz), 57.2 kHz, 60.0 Hz
[    85.124] (II) VBoxVideo(0): Modeline "VBoxDynamicMode"x0.0   66.10  1150 1152 1154 1156  947 949 951 953 (57.2 kHz)
[    85.124] (**) VBoxVideo(0):  Built-in mode "VBox-1024x768": 47.8 MHz (scaled from 0.0 MHz), 46.4 kHz, 60.0 Hz
[    85.124] (II) VBoxVideo(0): Modeline "VBox-1024x768"x0.0   47.83  1024 1026 1028 1030  768 770 772 774 (46.4 kHz)
[    85.124] (**) VBoxVideo(0):  Built-in mode "VBox-800x600": 29.3 MHz (scaled from 0.0 MHz), 36.4 kHz, 60.0 Hz
[    85.124] (II) VBoxVideo(0): Modeline "VBox-800x600"x0.0   29.31  800 802 804 806  600 602 604 606 (36.4 kHz)
[    85.124] (**) VBoxVideo(0):  Built-in mode "VBox-640x480": 18.8 MHz (scaled from 0.0 MHz), 29.2 kHz, 60.0 Hz
[    85.124] (II) VBoxVideo(0): Modeline "VBox-640x480"x0.0   18.84  640 642 644 646  480 482 484 486 (29.2 kHz)
[    85.124] (**) VBoxVideo(0):  Built-in mode "1150x947": 66.1 MHz (scaled from 0.0 MHz), 57.2 kHz, 60.0 Hz
[    85.124] (II) VBoxVideo(0): Modeline "1150x947"x0.0   66.10  1150 1152 1154 1156  947 949 951 953 (57.2 kHz)
[    85.124] (**) VBoxVideo(0):  Built-in mode "1024x768": 47.8 MHz (scaled from 0.0 MHz), 46.4 kHz, 60.0 Hz
[    85.124] (II) VBoxVideo(0): Modeline "1024x768"x0.0   47.83  1024 1026 1028 1030  768 770 772 774 (46.4 kHz)
[    85.124] (**) VBoxVideo(0):  Built-in mode "832x624": 31.7 MHz (scaled from 0.0 MHz), 37.8 kHz, 60.0 Hz
[    85.124] (II) VBoxVideo(0): Modeline "832x624"x0.0   31.68  832 834 836 838  624 626 628 630 (37.8 kHz)
[    85.124] (**) VBoxVideo(0):  Built-in mode "800x600": 29.3 MHz (scaled from 0.0 MHz), 36.4 kHz, 60.0 Hz
[    85.124] (II) VBoxVideo(0): Modeline "800x600"x0.0   29.31  800 802 804 806  600 602 604 606 (36.4 kHz)
[    85.124] (**) VBoxVideo(0):  Built-in mode "720x400": 17.7 MHz (scaled from 0.0 MHz), 24.4 kHz, 60.0 Hz
[    85.124] (II) VBoxVideo(0): Modeline "720x400"x0.0   17.68  720 722 724 726  400 402 404 406 (24.4 kHz)
[    85.124] (**) VBoxVideo(0):  Built-in mode "640x480": 18.8 MHz (scaled from 0.0 MHz), 29.2 kHz, 60.0 Hz
[    85.124] (II) VBoxVideo(0): Modeline "640x480"x0.0   18.84  640 642 644 646  480 482 484 486 (29.2 kHz)
[    85.124] (**) VBoxVideo(0):  Built-in mode "640x350": 13.8 MHz (scaled from 0.0 MHz), 21.4 kHz, 60.0 Hz
[    85.124] (II) VBoxVideo(0): Modeline "640x350"x0.0   13.80  640 642 644 646  350 352 354 356 (21.4 kHz)
[    85.124] (==) VBoxVideo(0): RGB weight 888
[    85.124] (==) VBoxVideo(0): Default visual is TrueColor
[    85.124] (==) VBoxVideo(0): Using gamma correction (1.0, 1.0, 1.0)
[    85.124] (==) VBoxVideo(0): DPI set to (96, 96)
[    85.124] (II) UnloadModule: "vesa"
[    85.124] (II) Unloading vesa
[    85.124] (II) UnloadModule: "fbdev"
[    85.124] (II) Unloading fbdev
[    85.124] (II) UnloadModule: "fbdevhw"
[    85.124] (II) Unloading fbdevhw
[    85.124] (--) Depth 24 pixmap format is 32 bpp
[    85.125] (II) Loading sub module "int10"
[    85.125] (II) LoadModule: "int10"
[    85.125] (II) Loading /usr/lib/xorg/modules/libint10.so
[    85.125] (II) Module int10: vendor="X.Org Foundation"
[    85.125]     compiled for 1.10.1, module version = 1.0.0
[    85.125]     ABI class: X.Org Video Driver, version 10.0
[    85.125] (II) VBoxVideo(0): initializing int10
[    85.127] (II) VBoxVideo(0): Primary V_BIOS segment is: 0xc000
[    85.138] (II) VBoxVideo(0): VESA BIOS detected
[    85.138] (II) VBoxVideo(0): VESA VBE Version 2.0
[    85.138] (II) VBoxVideo(0): VESA VBE Total Mem: 19456 kB
[    85.138] (II) VBoxVideo(0): VESA VBE OEM: VirtualBox VBE BIOS http://www.virtualbox.org/
[    85.138] (II) VBoxVideo(0): VESA VBE OEM Software Rev: 0.2
[    85.138] (II) VBoxVideo(0): VESA VBE OEM Vendor: Oracle Corporation
[    85.138] (II) VBoxVideo(0): VESA VBE OEM Product: Oracle VM VirtualBox VBE Adapter
[    85.138] (II) VBoxVideo(0): VESA VBE OEM Product Rev: Oracle VM VirtualBox Version 4.0.10_Debian
[    85.163] (==) VBoxVideo(0): Default visual is TrueColor
[    85.163] (EE) VBoxVideo(0): Disabling DRI due to missing server functionality.
[    85.163] (II) VBoxVideo(0): visual configurations initialized
[    85.163] (==) VBoxVideo(0): Backing store disabled
[    85.164] (II) VBoxVideo(0): Requested monitor count: 1
[    85.164] (II) VBoxVideo(0): Output VBOX0 using monitor section Configured Monitor
[    85.164] (II) VBoxVideo(0): Output VBOX0 has no monitor section
[    85.166] (II) VBoxVideo(0): EDID for output VBOX0
[    85.166] (II) VBoxVideo(0): Manufacturer: VBX  Model: 0  Serial#: 62063742
[    85.166] (II) VBoxVideo(0): Year: 1990  Week: 1
[    85.166] (II) VBoxVideo(0): EDID Version: 1.3
[    85.166] (II) VBoxVideo(0): Digital Display Input
[    85.166] (II) VBoxVideo(0): Indeterminate output size
[    85.166] (II) VBoxVideo(0): Gamma: 2.20
[    85.166] (II) VBoxVideo(0): DPMS capabilities: StandBy Suspend Off
[    85.166] (II) VBoxVideo(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    85.166] (II) VBoxVideo(0): Default color space is primary color space
[    85.166] (II) VBoxVideo(0): First detailed timing is preferred mode
[    85.166] (II) VBoxVideo(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
[    85.166] (II) VBoxVideo(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
[    85.166] (II) VBoxVideo(0): Manufacturer's mask: 0
[    85.166] (II) VBoxVideo(0): Supported detailed timing:
[    85.166] (II) VBoxVideo(0): clock: 66.1 MHz   Image Size:  0 x 0 mm
[    85.166] (II) VBoxVideo(0): h_active: 1150  h_sync: 1152  h_sync_end 1154 h_blank_end 1156 h_border: 0
[    85.166] (II) VBoxVideo(0): v_active: 947  v_sync: 949  v_sync_end 951 v_blanking: 953 v_border: 0
[    85.166] (II) VBoxVideo(0): Ranges: V min: 0 V max: 200 Hz, H min: 0 H max: 200 kHz, PixClock max 1005 MHz
[    85.166] (II) VBoxVideo(0): Monitor name: VBOX monitor
[    85.166] (II) VBoxVideo(0): EDID (in hex):
[    85.166] (II) VBoxVideo(0):     00ffffffffffff00585800007e04b303
[    85.166] (II) VBoxVideo(0):     0100010380000078eeee91a3544c9926
[    85.166] (II) VBoxVideo(0):     0f505400000001010101010101010101
[    85.166] (II) VBoxVideo(0):     010101010101d2197e0640b306300202
[    85.166] (II) VBoxVideo(0):     2200000000000000000000fd0000c800
[    85.166] (II) VBoxVideo(0):     c864000a202020202020000000fc0056
[    85.166] (II) VBoxVideo(0):     424f58206d6f6e69746f720a00000010
[    85.166] (II) VBoxVideo(0):     000a202020202020202020202020006f
[    85.166] (II) VBoxVideo(0): EDID vendor "VBX", prod id 0
[    85.166] (II) VBoxVideo(0): DDCModeFromDetailedTiming: 1150x947 Warning: We only handle separate sync.
[    85.166] (II) VBoxVideo(0): Using hsync ranges from config file
[    85.166] (II) VBoxVideo(0): Using vrefresh ranges from config file
[    85.167] (II) VBoxVideo(0): Printing DDC gathered Modelines:
[    85.167] (II) VBoxVideo(0): Modeline "1150x947"x0.0   66.10  1150 1152 1154 1156  947 949 951 953 -hsync -vsync (57.2 kHz)
[    85.167] (II) VBoxVideo(0): Printing probed modes for output VBOX0
[    85.167] (II) VBoxVideo(0): Modeline "1150x947"x60.0   66.10  1150 1152 1154 1156  947 949 951 953 (57.2 kHz)
[    85.167] (II) VBoxVideo(0): Modeline "1024x768"x60.0   47.83  1024 1026 1028 1030  768 770 772 774 (46.4 kHz)
[    85.167] (II) VBoxVideo(0): Modeline "832x624"x60.0   31.68  832 834 836 838  624 626 628 630 (37.8 kHz)
[    85.167] (II) VBoxVideo(0): Modeline "800x600"x60.0   29.31  800 802 804 806  600 602 604 606 (36.4 kHz)
[    85.167] (II) VBoxVideo(0): Modeline "640x480"x60.0   18.84  640 642 644 646  480 482 484 486 (29.2 kHz)
[    85.167] (II) VBoxVideo(0): Modeline "720x400"x60.0   17.68  720 722 724 726  400 402 404 406 (24.4 kHz)
[    85.167] (II) VBoxVideo(0): Modeline "640x350"x60.0   13.80  640 642 644 646  350 352 354 356 (21.4 kHz)
[    85.167] (II) VBoxVideo(0): Output VBOX0 connected
[    85.167] (II) VBoxVideo(0): Using user preference for initial modes
[    85.167] (II) VBoxVideo(0): Output VBOX0 using initial mode 1150x947
[    85.167] (II) VBoxVideo(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    85.167] (II) VBoxVideo(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    85.169] (==) VBoxVideo(0): DPMS enabled
[    85.169] (--) RandR disabled
[    85.169] (II) Initializing built-in extension Generic Event Extension
[    85.169] (II) Initializing built-in extension SHAPE
[    85.169] (II) Initializing built-in extension MIT-SHM
[    85.169] (II) Initializing built-in extension XInputExtension
[    85.169] (II) Initializing built-in extension XTEST
[    85.169] (II) Initializing built-in extension BIG-REQUESTS
[    85.169] (II) Initializing built-in extension SYNC
[    85.169] (II) Initializing built-in extension XKEYBOARD
[    85.169] (II) Initializing built-in extension XC-MISC
[    85.169] (II) Initializing built-in extension SECURITY
[    85.169] (II) Initializing built-in extension XINERAMA
[    85.169] (II) Initializing built-in extension XFIXES
[    85.169] (II) Initializing built-in extension RENDER
[    85.170] (II) Initializing built-in extension RANDR
[    85.170] (II) Initializing built-in extension COMPOSITE
[    85.170] (II) Initializing built-in extension DAMAGE
[    85.170] (II) Initializing built-in extension GESTURE
[    85.176] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    85.186] (II) VBoxVideo(0): Setting screen physical size to 304 x 250
[    85.316] (II) XKB: generating xkmfile /tmp/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    85.377] (II) Using input driver 'vboxmouse' for 'Configured Mouse'
[    85.377] (II) Loading /usr/lib/xorg/modules/input/vboxmouse_drv.so
[    85.377] (**) Option "CorePointer"
[    85.377] (**) Configured Mouse: always reports core events
[    85.377] (**) Configured Mouse: Device: "/dev/vboxguest"
[    85.377] (II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
[    85.378] (**) Configured Mouse: (accel) keeping acceleration scheme 1
[    85.378] (**) Configured Mouse: (accel) acceleration profile 0
[    85.378] (**) Configured Mouse: (accel) acceleration factor: 2.000
[    85.378] (**) Configured Mouse: (accel) acceleration threshold: 4
[    85.378] (II) Configured Mouse: On.
[    85.391] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    85.391] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    85.391] (II) LoadModule: "evdev"
[    85.391] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    85.392] (II) Module evdev: vendor="X.Org Foundation"
[    85.392]     compiled for 1.10.0.902, module version = 2.6.0
[    85.392]     Module class: X.Org XInput Driver
[    85.392]     ABI class: X.Org XInput driver, version 12.3
[    85.392] (II) Using input driver 'evdev' for 'Power Button'
[    85.393] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    85.393] (**) Power Button: always reports core events
[    85.393] (**) Power Button: Device: "/dev/input/event0"
[    85.393] (--) Power Button: Found keys
[    85.393] (II) Power Button: Configuring as keyboard
[    85.393] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input0/event0"
[    85.393] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    85.393] (**) Option "xkb_rules" "evdev"
[    85.393] (**) Option "xkb_model" "pc105"
[    85.393] (**) Option "xkb_layout" "us"
[    85.393] (**) Option "xkb_options" "lv3:ralt_switch"
[    85.396] (II) XKB: generating xkmfile /tmp/server-0C76CA335E924C2441A31FBFED02D59A89874CA6.xkm
[    85.440] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    85.441] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    85.441] (II) Using input driver 'evdev' for 'Sleep Button'
[    85.441] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    85.441] (**) Sleep Button: always reports core events
[    85.441] (**) Sleep Button: Device: "/dev/input/event1"
[    85.441] (--) Sleep Button: Found keys
[    85.441] (II) Sleep Button: Configuring as keyboard
[    85.441] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSLPBN:00/input/input1/event1"
[    85.441] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    85.441] (**) Option "xkb_rules" "evdev"
[    85.441] (**) Option "xkb_model" "pc105"
[    85.441] (**) Option "xkb_layout" "us"
[    85.441] (**) Option "xkb_options" "lv3:ralt_switch"
[    85.449] (II) config/udev: Adding input device VirtualBox USB Tablet (/dev/input/event3)
[    85.449] (**) VirtualBox USB Tablet: Applying InputClass "evdev pointer catchall"
[    85.449] (II) Using input driver 'evdev' for 'VirtualBox USB Tablet'
[    85.449] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    85.449] (**) VirtualBox USB Tablet: always reports core events
[    85.449] (**) VirtualBox USB Tablet: Device: "/dev/input/event3"
[    85.450] (--) VirtualBox USB Tablet: Found 9 mouse buttons
[    85.450] (--) VirtualBox USB Tablet: Found scroll wheel(s)
[    85.450] (--) VirtualBox USB Tablet: Found relative axes
[    85.450] (--) VirtualBox USB Tablet: Found absolute axes
[    85.451] (II) evdev-grail: failed to open grail, no gesture support
[    85.451] (--) VirtualBox USB Tablet: Found x and y absolute axes
[    85.451] (II) VirtualBox USB Tablet: Configuring as mouse
[    85.451] (II) VirtualBox USB Tablet: Adding scrollwheel support
[    85.451] (**) VirtualBox USB Tablet: YAxisMapping: buttons 4 and 5
[    85.452] (**) VirtualBox USB Tablet: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    85.452] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:06.0/usb1/1-1/1-1:1.0/input/input3/event3"
[    85.452] (II) XINPUT: Adding extended input device "VirtualBox USB Tablet" (type: MOUSE)
[    85.452] (EE) VirtualBox USB Tablet: failed to initialize for relative axes.
[    85.452] (II) VirtualBox USB Tablet: initialized for absolute axes.
[    85.452] (**) VirtualBox USB Tablet: (accel) keeping acceleration scheme 1
[    85.452] (**) VirtualBox USB Tablet: (accel) acceleration profile 0
[    85.452] (**) VirtualBox USB Tablet: (accel) acceleration factor: 2.000
[    85.452] (**) VirtualBox USB Tablet: (accel) acceleration threshold: 4
[    85.453] (II) config/udev: Adding input device VirtualBox USB Tablet (/dev/input/js0)
[    85.453] (II) No input driver/identifier specified (ignoring)
[    85.453] (II) config/udev: Adding input device VirtualBox USB Tablet (/dev/input/mouse0)
[    85.453] (II) No input driver/identifier specified (ignoring)
[    85.455] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    85.455] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    85.455] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    85.455] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    85.455] (**) AT Translated Set 2 keyboard: always reports core events
[    85.456] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    85.456] (--) AT Translated Set 2 keyboard: Found keys
[    85.456] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    85.456] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    85.456] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    85.456] (**) Option "xkb_rules" "evdev"
[    85.456] (**) Option "xkb_model" "pc105"
[    85.456] (**) Option "xkb_layout" "us"
[    85.456] (**) Option "xkb_options" "lv3:ralt_switch"
[    85.457] (II) config/udev: Adding input device ImExPS/2 Generic Explorer Mouse (/dev/input/event4)
[    85.457] (**) ImExPS/2 Generic Explorer Mouse: Applying InputClass "evdev pointer catchall"
[    85.457] (II) Using input driver 'evdev' for 'ImExPS/2 Generic Explorer Mouse'
[    85.457] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    85.457] (**) ImExPS/2 Generic Explorer Mouse: always reports core events
[    85.457] (**) ImExPS/2 Generic Explorer Mouse: Device: "/dev/input/event4"
[    85.457] (--) ImExPS/2 Generic Explorer Mouse: Found 9 mouse buttons
[    85.457] (--) ImExPS/2 Generic Explorer Mouse: Found scroll wheel(s)
[    85.457] (--) ImExPS/2 Generic Explorer Mouse: Found relative axes
[    85.457] (--) ImExPS/2 Generic Explorer Mouse: Found x and y relative axes
[    85.457] (II) ImExPS/2 Generic Explorer Mouse: Configuring as mouse
[    85.457] (II) ImExPS/2 Generic Explorer Mouse: Adding scrollwheel support
[    85.457] (**) ImExPS/2 Generic Explorer Mouse: YAxisMapping: buttons 4 and 5
[    85.457] (**) ImExPS/2 Generic Explorer Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    85.457] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input4/event4"
[    85.457] (II) XINPUT: Adding extended input device "ImExPS/2 Generic Explorer Mouse" (type: MOUSE)
[    85.458] (II) ImExPS/2 Generic Explorer Mouse: initialized for relative axes.
[    85.458] (**) ImExPS/2 Generic Explorer Mouse: (accel) keeping acceleration scheme 1
[    85.458] (**) ImExPS/2 Generic Explorer Mouse: (accel) acceleration profile 0
[    85.458] (**) ImExPS/2 Generic Explorer Mouse: (accel) acceleration factor: 2.000
[    85.458] (**) ImExPS/2 Generic Explorer Mouse: (accel) acceleration threshold: 4
[    85.458] (II) config/udev: Adding input device ImExPS/2 Generic Explorer Mouse (/dev/input/mouse1)
[    85.458] (II) No input driver/identifier specified (ignoring)
[    85.469] (II) config/udev: Adding input device (unnamed) (/dev/vboxguest)
[    85.469] (**) (unnamed): Applying InputClass "vboxmouse"
[    85.469] (II) Using input driver 'vboxmouse' for '(unnamed)'
[    85.469] (II) Loading /usr/lib/xorg/modules/input/vboxmouse_drv.so
[    85.469] (**) (unnamed): always reports core events
[    85.469] (**) (unnamed): Device: "/dev/vboxguest"
[    85.469] (**) Option "config_info" "udev:/sys/devices/virtual/misc/vboxguest"
[    85.469] (II) XINPUT: Adding extended input device "(unnamed)" (type: MOUSE)
[    85.469] (**) (unnamed): (accel) keeping acceleration scheme 1
[    85.469] (**) (unnamed): (accel) acceleration profile 0
[    85.469] (**) (unnamed): (accel) acceleration factor: 2.000
[    85.469] (**) (unnamed): (accel) acceleration threshold: 4
[    85.469] (II) (unnamed): On.

```

In my /etc/X11/xorg.conf, I added this to make X find the right library for GL:
```

Section "Files"
    ModulePath "/usr/lib/nvidia-96/xorg"
    ModulePath "/usr/lib/xorg/modules"
EndSection
```

It seems to me that X now uses the nvidia library. Can someone point me in the right direction?

thanks in advance, rudd

---

### Post by danielbauwens on 2012-10-26
Open a terminal and type this:

```
sudo apt-get install nvidia-current
```
and then reboot.

Daniel

---

### Post by dino99 on 2012-10-26
virtualbox is only doing emulation, dont expect too much.
If your wish is to use ubuntu (linux) then your next step is to do a real installation.

[http://ubuntuforums.org/showpost.php?p=11843514&postcount=9](http://ubuntuforums.org/showpost.php?p=11843514&postcount=9)

---

### Post by r144 on 2012-10-26
hi Daniel,

thanks for your quick reply. I did follow your suggestion. I did change my xorg.conf to load the nvidia-current module. Now /var/log/Xorg.0.log says

```
[   189.988] (II) LoadModule: "glx"
[   189.988] (II) Loading /usr/lib/nvidia-current/xorg/libglx.so
[   190.019] (EE) Failed to load /usr/lib/nvidia-current/xorg/libglx.so: libnvidia-tls.so.270.41.06: cannot open shared object file: No such file or directory
[   190.024] (EE) LoadModule: Module glx does not have a glxModuleData data object.
[   190.025] (II) UnloadModule: "glx"
[   190.025] (II) Unloading glx

```

Do I need other packages?

rudd

---

### Post by QIII on 2012-10-26
Virtualbox does not use the host's GPU directly.  It uses a hardware virtualization layer and the "graphics card" it uses is one from InnoTek Systemberatung GmbH.  Adding the driver for the host's GPU will at best do nothing.  At worst it will mess things up.

I don't know if adding the Guest Additions will get you OpenGL support.

You are limited to the InnoTek adapter in the virtualization layer nonetheless.  If it doesn't support OpenGL, it doesn't.

---

### Post by r144 on 2012-10-26
Well, that's clear then. I uninstall freecad and nvidia-current.

Thanks for your reply, rudd

---

### Post by r144 on 2012-10-26
solved it.
I found on some site the text

> For those wondering about the technical implementation of this  3D support, the documentation describes it as, "Technically, VirtualBox implements  this by installing an additional hardware 3D driver inside your guest when the  Guest Additions are installed.

The checkbox 3D acceleration was ticked, but it has to be ticked at the moment the guest additiions are installed, which it wasn't. So I uninstalled the guest additions and reinstalled them (virtualbox-ose-guest-dkms and virtualbox-ose-guest-utils). After a reboot the message was gone and I am able to run freecad.

Rudd

---

