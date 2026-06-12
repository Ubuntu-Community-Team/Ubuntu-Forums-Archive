---
title: "Edgy+fglrx+rendering"
date: 2006-12-01
forum: General Help
---

### Post by Jijua on 2006-12-01
Hi all!
I just upgraded to Edgy and everything went smooth except enabling 3D rendering.
I have an ATI Radeon 9100 card on a Nvidia Nforce2 motherboard, equipped with an AMD Athlon XP 2600+ Barton.
The problem is that I cannot gain 3D rendering in any way:
```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
```
```
$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

```
The fglrx driver is the one from the edgy repository, but the problem is the same with the ATI proprietary driver.
These are some pieces of my Xorg.0.log file, filtered to highlight the most important errors:

```
(EE) fglrx(0): DRIScreenInit failed!
(EE) Error loading keymap /var/lib/xkb/server-0.xkm
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(WW) fglrx(0): Failed to open DRM connection
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) Loading extension XFree86-DRI
(==) fglrx(0): NoDRI = NO
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
(II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
	ABI class: X.Org XInput driver, version 0.6
	ABI class: X.Org XInput driver, version 0.6
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.28.1.1.2.3-driver-lnx-x86-x86_64-287161
drmOpenDevice: node name is /dev/dri/card0
(==) fglrx(0): OpenGL ClientDriverName: "atiogl_a_dri.so"
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
```
Please note that I have disabled the "Composite" extension (not supported by ATI nowadays) as well as the AIGLX feature (I don't want to use it, but the problem comes out also with AIGLX enabled), as stated in my xorg.conf file:

```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "dbe"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "record"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "it"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	HorizSync    30.0 - 65.0
	VertRefresh  50.0 - 75.0
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option "VideoOverlay" "on"
	Option "OpenGLOverlay" "off"
#INIZIO EDITING
	Option "no_accel" "no"
#	Option "no_dri" "no"
	Option "mtrr" "on"
	Option "DesktopSetup" "Single"
	Option "ScreenOverlap" "0"
	Option "Capabilities" "0x00000800" #modified to 800 from 000
	Option "CapabilitiesEx" "0x00000000"
	Option "CenterMode" "off"
	Option "PseudoColorVisuals" "off"
	Option  "Stereo" "off"
	Option  "StereoSyncEnable" "1"
	Option  "FSAAEnable" "no"
	Option  "FSAAScale" "1"
	Option  "FSAADisableGamma" "no"
	Option  "FSAACustomizeMSPos" "no"
	Option  "FSAAMSPosX0" "0.000000"
	Option  "FSAAMSPosY0" "0.000000"
	Option  "FSAAMSPosX1" "0.000000"
	Option  "FSAAMSPosY1" "0.000000"
	Option  "FSAAMSPosX2" "0.000000"
	Option  "FSAAMSPosY2" "0.000000"
	Option  "FSAAMSPosX3" "0.000000"
	Option  "FSAAMSPosY3" "0.000000"
	Option  "FSAAMSPosX4" "0.000000"
	Option  "FSAAMSPosY4" "0.000000"
	Option  "FSAAMSPosX5" "0.000000"
	Option  "FSAAMSPosY5" "0.000000"
	Option  "UseFastTLS" "0"
	Option  "BlockSignalsOnLock" "on"
	Option  "UseInternalAGPGART" "no"
	Option  "ForceGenericCPU" "no"
	Option  "KernelModuleParm" "locked-userpages=0" #modified from "agplock=0"
	Option  "backingstore" "true"
#FINE EDITING
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "ServerFlags"
	Option "AIGLX" "off"
EndSection

Section "Extensions"
	Option	"Composite" "0"
EndSection

```

I've spent a lot of time trying to understand what's wrong, but with no success. Consider that if I choose to run the X server with the open-source "ati" driver I can get the rendering on and play games freely. But, I just cannot see any movie, using any of the players available. I can only hear sound but no image at all, just a fixed black.
Coming back with the fglrx driver I get the video bun no 3D rendering :-| 
Any idea why?

---

### Post by Jijua on 2006-12-01
Just to add some more informations:
```
$ dmesg | grep fglrx
[17179599.876000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179599.876000] [fglrx] Maximum main memory to use for locked dma buffers: 680 MBytes.
[17179599.876000] [fglrx:firegl_init_module] *ERROR* firegl_stub_register failed
[17179655.964000] [fglrx] Maximum main memory to use for locked dma buffers: 680 MBytes.
[17179655.964000] [fglrx:firegl_init_module] *ERROR* firegl_stub_register failed
[17179659.596000] [fglrx] Maximum main memory to use for locked dma buffers: 680 MBytes.
[17179659.596000] [fglrx:firegl_init_module] *ERROR* firegl_stub_register failed
[17186778.656000] [fglrx] Maximum main memory to use for locked dma buffers: 680 MBytes.
[17186778.656000] [fglrx:firegl_init_module] *ERROR* firegl_stub_register failed
[17186782.120000] [fglrx] Maximum main memory to use for locked dma buffers: 680 MBytes.
[17186782.120000] [fglrx:firegl_init_module] *ERROR* firegl_stub_register failed

```
I don't know what kind of errors are...
```
$ modinfo fglrx
filename:       /lib/modules/2.6.17-10-386/volatile/fglrx.ko
vermagic:       2.6.17-10-386 mod_unload 486 REGPARM gcc-4.1
depends:        agpgart
author:         Fire GL - ATI Research GmbH, Germany
description:    ATI Fire GL
license:        Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY
parm:           firegl:charp

```
and my kernel is the correct one (2.6.17-10)...
```
$ lsmod | grep agp
nvidia_agp              8732  1 
agpgart                33456  2 drm,nvidia_agp

```
the agp module is loaded...
```
$ lsmod | grep fglrx
$ 

```
but the fglrx module is not.

---

### Post by wpshooter on 2006-12-01
The first thing that strikes me is that you are using an ATI video card on a Nvidia motherboard !!!

Humor me and if you have one, replace your ATI video card with a Nvidia one and then I would reinstall the O/S and see if your problems do not go away.

---

### Post by Jijua on 2006-12-01
Not properly a great approach to the problem...
Anyway, the failure seems related to the "drm" module which was loaded at boot. I removed it and rebooted.
The fglrx module is now loaded properly (even if I don't have it among the modules to be loaded at start-up in /etc/modules...)
However, I now have 3D rendering and definitely no errors at all in Xorg.0.log!!! :D 

BUT....

After I try to use the desktop (i.e. open a folder) the system suddenly gets frozen: no keybord response, I only have the curson available, but no possibility to do anything. The only way to escape is to get a hard reset.

The situation goes on every time the fglrx module is loaded: if I put it among the forbidden modules or if I reload the drm module, the hardlocks disappear, but with them also the 3D rendering ...](*,) 

Any idea?

---

### Post by qamelian on 2006-12-01
I think if you check the documentation on the ATI site you'll find that hardware 3D is not supported by the FGLRX drivers for your card.

---

### Post by Jijua on 2006-12-02
Actually it is supported, by driver version 8.28.8 which is the one I have installed...

---

### Post by Jijua on 2006-12-02
Bump,
any idea for the hardlocks?

---

### Post by Jijua on 2006-12-03
I go on having freezes...
bump

---

### Post by Jijua on 2006-12-04
Bump

---

### Post by juraj on 2006-12-04
I have freezes too with fglrx, however I get them occasionaly after logging out. Sorry, but I can't help you. ;)

BTW a safe way to restart a linux system when it hangs, and provided that kernel is still barely alive, is to press and hold alt and print screen (sysrq), and then while holding press S, then U, then B (all while holding alt and print screen). This syncs all filesystems and remounts them read-only. And then it restarts the machine.

---

### Post by Jijua on 2006-12-08
re-bump.
Any idea for the freeze?????

---

### Post by randytuggle on 2006-12-08
try installing automatix2 bleeder. It has the latest drivers for ATI and Nvidia cards. [http://getautomatix.com](http://getautomatix.com)

---

### Post by TDsai on 2006-12-09
i had exactly the same symptoms before: (system suddenly gets frozen: no keybord response, I only have the curson available, but no possibility to do anything. The only way to escape is to get a hard reset.)

had nothing to do with ati drivers though but might be similar.. the cause is that i change the driver for my wireless card and i forgot to blacklist and delete some old deb files. 

sorry i cant tell u how for fglrx drivers i think u need to edit /etc/default/linux-restricted-modules-common and add fglrx                                   on the DISABLED_MODULES 

look here for better info:
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

---

### Post by engage on 2006-12-13
[COLOR="Silver"]I think that composite extension is enabled by default so try this:

**sudo gedit /etc/X11/xorg.conf**

and paste this at the end of the file:

[B]Section "Extensions"
        Option "Composite" "false"
EndSection[/B]

it is a solution for me.

(and sorry for my english ](*,)  )[/COLOR]

sorry a don't have seen your xorg.conf :)

---

### Post by engage on 2006-12-13
As above :P

---

