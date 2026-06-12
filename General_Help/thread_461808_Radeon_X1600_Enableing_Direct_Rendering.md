---
title: "Radeon X1600 Enableing Direct Rendering"
date: 2007-06-02
forum: General Help
---

### Post by The Creator on 2007-06-02
I need help enabling direct rendering on my radeon x1600. I have configured xorg to use flgrx, installed the drivers off ati's website (latest ones), and done the aticonfig --initial to configure the card. 

Here is the output for glxinfo
```
john@john-desktop:~$ glxinfo
name of display: :0.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
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
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
john@john-desktop:~$ 

```

and here is my xorg.conf


```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "vbe"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "off"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 51.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Radeon X1600"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Radeon X1600"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection
```

Any help would be greatly apreciated :) Thanks in advance! May the source be with you!

---

### Post by The Creator on 2007-06-02
bump... please help me, it is urgent

---

### Post by The Creator on 2007-06-02
please please please please, i really need help. Even if someone comes and sais they read my post please even acknowledgement! AHHHHH I FEEL LONLELY

---

### Post by Rajiv_Nair on 2007-06-02
i dont think ur ATI driver install was clean. To confirm run > fglrxinfo from terminal. If it tells u stuff about ATI then well and good. If it says "MESA" then it means you install wasnt successful. If ur using feisty fawn(ubuntu 7.04) i think its better to stick with the driver thats available from "system->administration->Restricted drivers manager"

For a detailed walkthrough take a luk at [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide) and follow METHOD 1 suggested there :)

---

### Post by The Creator on 2007-06-02
john@john-desktop:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)


i followed version 2 there...

---

### Post by Rajiv_Nair on 2007-06-02
try running

> aticonfig --initial --force

and reboot ur system

---

### Post by The Creator on 2007-06-02
will do, i just followed version one and it didnt help.

i get the following:

john@john-desktop:~$ aticonfig --initial --force
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-2
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.
john@john-desktop:~$

---

### Post by The Creator on 2007-06-02
o yeah, when i used the ati proprietary drivers i could boot with the old feisty kernel but the new one i got via software update stops me from booting.

---

### Post by Rajiv_Nair on 2007-06-02
try prefixing sudo to the ati config --initial --force command and reboot :-?

---

### Post by The Creator on 2007-06-02
didnt work. and my newer kernel still wont boot with it. Should i try uninstalling all my ati drivers then try the ones out of the repositry?

---

### Post by The Creator on 2007-06-02
o yeah, how do i remove the drivers?

---

### Post by Rajiv_Nair on 2007-06-02
>  Revert to Xorg driver

If (for any reason) the fglrx install fails, you can revert to the Xorg driver by executing

sudo dpkg-reconfigure xserver-xorg

and selecting the "ati" driver, or simply restoring the previous /etc/X11/xorg.conf file, if you made a backup.

You also need to remove the xorg-driver-fglrx or your manually installed drivers to get the 3D acceleration back, since it is provided by file /usr/lib/libGL.so.1.2 which belongs to libgl1-mesa package and which is moved to backup and replaced at the installation of xorg-driver-fglrx (or the manually built) package. In case the removal of the fglrx drivers fails to restore the file from libgl1-mesa, you have to reinstall the package by running:

sudo apt-get install --reinstall libgl1-mesa

That was from the unofficial ubuntu driver wiki. :)

---

### Post by The Creator on 2007-06-02
will i get the direct draw on my x1600 if i use the xorg ati driver? Will i be able to run beryl and use cedega?

---

### Post by Rajiv_Nair on 2007-06-02
i though directdraw was a directx feature:D. If u use the Xorg ATI driver ull be able to run 2d apps without hassle. But beryl needs direct renedering capabilites. If u want to use beryl ull have to install the proprietary ATI drivers. Again i'd suggest installing from "System->Administration->Restricted drivers manager" and then run > sudo gedit /etc/X11/xorg.conf

then add the following lines to the end of that file

> Section "Extensions"
        Option  "Composite" "Disable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection

---

### Post by The Creator on 2007-06-02
i am installing it now, but it said it will only enable 2d acceration.

---

### Post by The Creator on 2007-06-02
thanks for all your help so far by the way, but i am only getting 2d acceration now. Beryl wont launch and i know the card is capable of it because it is an rv350 with 512 mb ddr2 ram at 500 megahertz.

---

### Post by The Creator on 2007-06-02
still no luck, is anyone here? how do i remove the ati fglrx?

---

### Post by kellemes on 2007-06-02
Try to do things slow..
step 1 = get fglrx going.
step 2 = get Beryl going, you need GLX for this.

fglrxinfo shows fglrx is not installed correctly so this is your main problem.
Please post /var/log/Xorg.0.log after failing to startup X.

---

### Post by Jacks0n on 2007-06-20
hm, i've had this before.. last time worked best when I just re-installed it completely. to remove it, type
```

sudo apt-get remove fglrx-kernel-source
sudo apt-get remove xorg-driver-fglrx
sudo apt-get remove xorg-driver-fglrx-dev

```

change the driver "fglrx" to "vesa" in /etc/X11/xorg.conf with this command
```
sudo sed -i 's/fglrx/vesa/g' /etc/X11/xorg.conf
```

and make sure you have the following at the end of /etc/X11/xorg.conf

```
Section "Extensions"
        Option  "Composite" "Disable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection
```

restart. and to install it (copying from the unofficial ati wiki.... do the following)
```
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) # (Okay if it is already installed)
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo sed -i 's/vesa/fglrx/g' /etc/X11/xorg.conf
```

do the following
```
cat /etc/default/linux-restricted-modules-common | grep DISABLED_MODULES | tail -1
```
and make sure there isn't a line that looks like DISABLED_MODULES="fglrx". if there is, do the following
```
sudo sed -i 's/fglrx//g' /etc/default/linux-restricted-modules-common
```

restart again and that should work. by the way, the fglrx driver doesn't support compositing so when beryl is working, there isn't any direct rendering. but that's normal. as long as fglrxinfo shows the fglrx driver, and not mesa

---

