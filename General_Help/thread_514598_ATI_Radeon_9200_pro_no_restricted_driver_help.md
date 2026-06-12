---
title: "ATI Radeon 9200 pro no restricted driver help?"
date: 2007-07-31
forum: General Help
---

### Post by Ripfox on 2007-07-31
I just installed on an old desktop and have an ati 9200 pro, I thought that it would show up like the other ati cards in the past in the "restricted drivers manager" but it says I don't need any restricted drivers...what gives here?

---

### Post by eggdeng on 2007-08-01
You're out of luck with this one. The fglrx driver doesn't support cards under 9500.The bundled ati driver is pretty good though.

---

### Post by Ripfox on 2007-08-01
Meaning the one installed by default in Feisty? I used to have an ATI 9200 Radeon AGP card back on Dapper, and I could have sworn I got fglrx going...I know I had Beryl running...

---

### Post by aldenhg on 2007-08-01
Don't bother. With an older ATI card you're better off using the open source radeon driver - it's the one that was probably installed by default. It has better support for older cards then fglrx and it's open source and therefore way awesomer.
If you're curious, you can always hit Alt-F2 and type in ```
gksudo gedit /etc/X11/xorg.conf
```  Once it's open, look for a line that says ```
Driver       "vesa"
```
or ```
Driver       "radeon"
```
If you find the radeon one, you're already running the good open source driver. If you find vesa, change it to radeon, save and restart. If something goes wrong and you can't get back in to a graphical session, just use the command line and type in ```
sudo nano /etc/X11/xorg.conf
``` and change the line back to vesa.

---

### Post by Ripfox on 2007-08-01
Driver		"ati"

Is that ALL I have to do, change it to "radeon"

---

### Post by aldenhg on 2007-08-02
Well, ati is the name of the old open source driver. I think that it loads the same driver as radeon. You can try radeon and it probably won't change anything. Try running glxgears in a terminal and see if it's choppy or not. If it's not, 3d is working porperly and you don't need to worry about it. You can also just try ```
glxinfo | grep direct
``` If it returns ```
direct rendering: Yes
```
you're in business.

---

### Post by eggdeng on 2007-08-02
I have an old box with Edgy running Beryl with aiglx on the ati driver. Sadly, the how-to I used at the Beryl Wiki has been down for a while.

---

### Post by Ripfox on 2007-08-02
Well. I get (direct rendering:yes)
And glxgears at like maybe 500-600 fps, (which sucks)
But why when I try to play Tibia do I get 

X Error of failed request:  GLXUnsupportedPrivateRequest
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  16 (X_GLXVendorPrivate)
  Serial number of failed request:  58
  Current serial number in output stream:  59

And Regnum says it's unsupported video card too...

Shouldn't these things work technically?  Especially Tibia which has weak graphics?

---

### Post by eggdeng on 2007-08-02
A quick google search for the minimum requirements for Tibia indicates that it requires DirectX i.e. W*n*d*s or Wine. Regnum seems to have issues with ATI cards. I think you are being a bit optimistic expecting good results from these on old hardware. In any case you would be better off posting on the forums for the games, where people will be more of aware of game-specific problems.

---

### Post by Ripfox on 2007-08-02
Well, I was just mentioning it in relation to my accelerated graphics problem...also, I am talking about the Tibia linux client.

---

### Post by Ripfox on 2007-08-03
Ok, this is getting confusing. Upon initial install, what driver would Feisty apply to an ATI 9200 PRO? I believe I was able to activate "desktop effects" with that configuration. (had it working at one point anyways)

Then I run into a post which says fglrx works for 8500 and above, but when I click on the link to the wiki it says 9500 and above. The first time I didn't notice this, and borked my xorg, so I sudo dpkg-reconfigure xserver-xorg, and choose ATI for the driver. Not even desktop effects will work after this.  So, I assume theres an older fglrx driver out there I could get going?

Any info would help me, and thanks again for sticking this out...

---

### Post by stchman on 2007-08-03
> **ripfox said:**
> I just installed on an old desktop and have an ati 9200 pro, I thought that it would show up like the other ati cards in the past in the "restricted drivers manager" but it says I don't need any restricted drivers...what gives here?

Have you tried Envy?

---

### Post by mabovo on 2007-08-03
> **aldenhg said:**
> Well, ati is the name of the old open source driver. I think that it loads the same driver as radeon. You can try radeon and it probably won't change anything. Try running glxgears in a terminal and see if it's choppy or not. If it's not, 3d is working porperly and you don't need to worry about it. You can also just try ```
glxinfo | grep direct
``` If it returns ```
direct rendering: Yes
```
you're in business.

Please, I have the ATI Radeon 9600 card but couldn't install 8.39.4 fglrx driver for some reason I don't know.
I've got the following message:

marcos@linux-ubuntu:~$ 
marcos@linux-ubuntu:~$ glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
marcos@linux-ubuntu:~$ 

How can I  fix this, my xorg.conf has "ati" instead of "fglrx". Sorry I'm newby on certain parts of Linux like setting system variables, paths, etc.

---

### Post by w4ett on 2007-08-03
The new fglrx only supports the 9500 cards and above. (I know it's been said before :)  )  I too have a 9200 and run the xorg driver ati....glxgears speed is 850-900 fps and also the GL Desktop (Desktop Effects) run pretty well, also Google Earth.

What happened to the driver is that feisty uses Xorg 7.2....the old Legacy card fglrx driver will only run under XFree86 and below, so it's incompatible with the current iteration of Ubuntu.

---

### Post by Ripfox on 2007-08-04
So how do i restore my original xorg that Feisty installed?

---

### Post by w4ett on 2007-08-04
In the terminal type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Select "ati' as the driver and then select your desired resolutions.  Restart x and you should have it back.

---

### Post by Ripfox on 2007-08-04
No, I did that and it did give me back X, but now desktop effects don't work and they did after the fresh install.

---

### Post by w4ett on 2007-08-04
a quick way to reset you xorg.conf back to default is to run the live cd and copy it's xorg.conf to your hard drive or to a flash drive and use it to replace you old one.

or you can reconfigure the entire xorg.conf :
```

sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Ripfox on 2007-08-04
Ah I will try that...but as I stated before, I did dpkg-reconfigure already, and it restored X, but with NO 3d acceleration. I had 3d acceleration with this card after the INITIAL install. What I am trying to do is get it back what little I had. I messed it up when I tried to install fglrx, and as this is a 9200, it did not work. Then I did the dpkg option, selected ATI, and NO acceleration.

---

### Post by Dubbayoo on 2007-08-04
> **aldenhg said:**
> Well, ati is the name of the old open source driver. I think that it loads the same driver as radeon. You can try radeon and it probably won't change anything. Try running glxgears in a terminal and see if it's choppy or not. If it's not, 3d is working porperly and you don't need to worry about it. You can also just try ```
glxinfo | grep direct
``` If it returns ```
direct rendering: Yes
```
you're in business.
What if it returns No? I have an 8500 with the ati driver. I've had this working in the past but haven't paid attention in a while.

---

### Post by aldenhg on 2007-08-04
Well, the 8500 has the R200 core and is supported by the open source driver, so it should just work. As always, check your xorg.conf file (/etc/x11/xorg.conf) to make sure that the driver you are using is either "ati" or "radeon." If it's vesa, then change it to one of the two. They're interchangeable, so it doesn't matter which one. Beyond that I don't really have a clue. I got pissed off at the lack of good support for my radeon 9800, so I switched to a nvidia 7600. HUGE upgrade in terms of performance and support in Linux. If 3d matters enough to you I'd reccomend picking up a new card. I'm guess you have an AGP mobo, so try out ebay for a 5600 or 6600.

---

### Post by Ripfox on 2007-08-05
Ok, but there IS a way to get 3d going (allbeit semi-slow) on this radeon 9200 pro. My point is, I HAD it going, I just borked it up! :) All I want to know is which is the right config to get it back...there has to be a tut somewhere, and I cannot seem to find it! Yes this is my own fault. :lolflag:

---

### Post by w4ett on 2007-08-05
For reference here's a copy of my  working xorg.conf for ATI Radeon 9200:

>  # /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Radeon 9200SE"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Dell E773c"
	Option		"DPMS"
	HorizSync	28-60
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Radeon 9200SE"
	Monitor		"Dell E773c"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by Ripfox on 2007-08-05
Ah...thank you. I will look this over and make the necessary changes.

---

### Post by w4ett on 2007-08-05
Another thought...if modifying your xorg.conf doesn't work, and you still get error messages regarding direct rendering,  you might try reinstalling xserver-xorg-core

---

### Post by Ripfox on 2007-08-05
Thats worth a try as well. Thanks, I will report back.

---

### Post by Ripfox on 2007-08-06
Ok...this is weird. My xorg is virtually identical to the one above, except the monitor. I still do not have 3d acceleration. What I cannot figure out is how I got it going before.  All the threads I have tried, and there were many, do not work.

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 x86/MMX/SSE TCL
OpenGL version string: 1.3 Mesa 6.5.2

glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
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
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 x86/MMX/SSE TCL
OpenGL version string: 1.3 Mesa 6.5.2
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
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x4b 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 630 Host (rev 21)
00:00.1 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:01.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
00:01.1 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 83)
00:01.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
00:01.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
00:01.4 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS PCI Audio Accelerator (rev 02)
00:02.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:09.0 Ethernet controller: Lite-On Communications Inc LNE100TX (rev 20)
00:0d.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
00:0d.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 630/730 PCI/AGP VGA Display Adapter (rev 21)


Theres all the info.

---

### Post by w4ett on 2007-08-06
Here's what you should be seeing:

> w4ett@w4ett-desktop:~$ fglrxinfo
The program 'fglrxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install xorg-driver-fglrx
Make sure you have the 'restricted' component enabled
bash: fglrxinfo: command not found
w4ett@w4ett-desktop:~$ 

Try this:
```

sudo apt-get remove xorg-driver-fglrx
```

make sure all modules from the restricted driver install attempts are removed, then reboot or restart x.

---

### Post by Ripfox on 2007-08-06
Awww Haaaw homie! 

 glxinfo | grep direct
direct rendering: Yes
joneser@joneser-desktop:~$ glxgears
2612 frames in 5.0 seconds = 522.384 FPS
2593 frames in 5.0 seconds = 518.572 FPS

THANK YOU. 
Sorry I am so slow here...guess those failed attempts at fglrx were what was screwin' with me.

So upward and onward...I have been reading about ways you can boost these frame-rates through some tinkering...am I out of luck on that front?

Once again, thanks for the help so far!

---

### Post by w4ett on 2007-08-06
> **ripfox said:**
> Awww Haaaw homie! 

 glxinfo | grep direct
direct rendering: Yes
joneser@joneser-desktop:~$ glxgears
2612 frames in 5.0 seconds = 522.384 FPS
2593 frames in 5.0 seconds = 518.572 FPS

THANK YOU. 
Sorry I am so slow here...guess those failed attempts at fglrx were what was screwin' with me.

So upward and onward...I have been reading about ways you can boost these frame-rates through some tinkering...am I out of luck on that front?

Once again, thanks for the help so far!

Those rates are pretty much average...I get 850-900 Fps on mine, but in reality, that's pretty respectable.  Probably due to bus throughput than the actual card IMO.  but at least you got it back...Good Luck!

---

### Post by atlacatl1978 on 2007-08-06
> **aldenhg said:**
> Well, ati is the name of the old open source driver. I think that it loads the same driver as radeon. You can try radeon and it probably won't change anything. Try running glxgears in a terminal and see if it's choppy or not. If it's not, 3d is working porperly and you don't need to worry about it. You can also just try ```
glxinfo | grep direct
``` If it returns ```
direct rendering: Yes
```
you're in business.

i did what u said above but i got No for rendering even though the driver bieng used by Feisty is radeon, can somebody help me please?

---

### Post by dougfractal on 2007-08-18
atlacatl1978,  ripfox and w4ett can you respond to this as I'm trying to help macduff with this board.

The last few days I've been working  a diagnostic tool

```
mkdir ~/Xinfo
cd ~/Xinfo
wget -O xinfo.sh  http://fractaldimension.org.uk/ubuntu/xinfo.txt
chmod a+x ./xinfo.sh
./xinfo.sh
```


please attach the ***xinfo.tar.gz**

view script
 [http://fractaldimension.org.uk/ubuntu/xinfo.txt](http://fractaldimension.org.uk/ubuntu/xinfo.txt)

---

### Post by w4ett on 2007-08-18
Here ya go.

---

