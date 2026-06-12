---
title: "[SOLVED] Dual Monitor DVI on 256MB ATI Radeon 2400 XT,"
date: 2007-12-20
forum: General Help
---

### Post by DouglasAWh on 2007-12-20
I am trying to get dual monitors working on a 256MB ATI Radeon 2400 XT in a Dell Optiplex 755.  In fact, the second monitor isn't even picked up in Screens and Graphics, but the signal is sent to both monitors.  As somewhat of an aside, I have never gotten dual monitors to work on any box, but this is a new machine so I thought I'd give it a shot.

Thanks!

---

### Post by danwood76 on 2007-12-20
Have you got the fglrx drivers installed correctly?
If so go into the catalyst control center and enable the second display and set it to extend the desktop.

Without these drivers you have no chance of enabling an extended desktop.

regards,
Danny

---

### Post by DouglasAWh on 2007-12-20
I followed the instructions at [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide), but don't see how to open catalyst.

EDIT: it appears as though I just installed the driver, I didn't see the instructions further below in the above page.  I'm working on it.

---

### Post by danwood76 on 2007-12-20
It should be under accesories in the application menu, if not press alt and F2 and run amdcccle.

If it doesnt work then you may not have installed correctly.

regards,
Danny

---

### Post by DouglasAWh on 2007-12-20
When I do 

> 
sudo aticonfig --overlay-type=Xv

    * Note: Alternative in the overlay-type to "Xv" can be "opengl" or "disable" if the TV-out makes problems in videos. 


I always get some output then "Aborted (core dumped)" then I have to 

sudo dpkg-reconfigure xserver-xorg.

While would I keep getting the aborted error?  Thanks again for the help!

---

### Post by danwood76 on 2007-12-20
Try just running sudo aticonfig --initial dont worry about the Xv overlay stuff

---

### Post by DouglasAWh on 2007-12-20
ok, I've got the catalyst showing up in Applications now, but when I click on it nothing happens...

fglrx does show up as my graphics driver in Screen and Graphics.

EDIT:

whitdoug@whitdoug-desktop:~$ amdcccle
amdcccle: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

---

### Post by CoolHand on 2007-12-20
> **DouglasAWh said:**
> I am trying to get dual monitors working on a 256MB ATI Radeon 2400 XT in a Dell Optiplex 755.  In fact, the second monitor isn't even picked up in Screens and Graphics, but the signal is sent to both monitors.  As somewhat of an aside, I have never gotten dual monitors to work on any box, but this is a new machine so I thought I'd give it a shot.

Thanks!

If you want it to act as one big desktop continued across monitors you are in luck.  First if your card supports it install the restricted driver for ati cards. (fglrx I think it is called). You can turn it on and install it through the menu under System/Administration/Restricted Drivers Manager.   With that comes a command line utility called aticonfig.  To be safe make a backup copy of your /etc/X11/xorg.conf file.  Then run the following command in a terminal:
sudo aticonfig --dtop=horizontal --overlay-on=1

This will alter your xorg config for a single big side by side desktop across both monitors.  Log out and then back in to activate it as X needs to restart with the new config.  Alternately you can force X to restart with ctrl-alt-backspace.

Took me about an hour to figure this out today myself but ati made it simple and it works well.  There are other options for aticonfig if you want a different layout.  Try aticonfig --help for all the info.

Hope that helps.

---

### Post by DouglasAWh on 2007-12-21
Won't be back at that PC until probably on or after January 2nd, so I'll post an update some time after that with whether I've gotten it working.

Thanks again for all the help!

---

### Post by larseven on 2008-01-09
I'm having the same problem (enabling dual screen using optiplex 755 with Radeon 2400 XT). Please let me now if you find a solution. 

Some one told me that while the old Radeon cards identified as two separate cards on the PCI bus, my new Radeon 2400 identifies as only one. Could this cause problems ?

---

### Post by Evdog on 2008-01-17
Did anyone get this to work yet? I have the same setup and have looked through numerous posts and still can not get it to work. In fact I cant get the radeon 1300 to work on my dell optiplex 755 either. I try to install the restricted driver from ati and it crash X. Any update on this????

---

### Post by DouglasAWh on 2008-01-17
I haven't had a free second to work on it, but I'll post when I do.  It probably won't be for a couple weeks though.

---

### Post by danwood76 on 2008-01-17
Just had a thought, what version of the ati driver is installed from the package manager?

You should try the latest version (8.443 or 7.12) as it will support the 2400 a lot better than the older version.
follow method 2 from this site:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

regards,
Danny

---

### Post by jayach on 2008-02-06
I have the exact same hardware.  I just upgraded from 7.04 and lost my dual setup
 (among other things).  I followed these guides w/o success:

[http://ubuntuforums.org/showthread.php?t=580748](http://ubuntuforums.org/showthread.php?t=580748)
and 
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

I was finally able to enable dual displays by this command, as suggested in this thread:

> **CoolHand said:**
> 
sudo aticonfig --dtop=horizontal --overlay-on=1


However, I do not have video acceleration.    I did not have it before (in 7.10 anyway - 7.04 worked fine), but is much more noticeable with dual displays now.  My system is completely unusable now, xgl takes 100% cpu just to type and watch for a minute while what I type slowly gets displayed on the screen.

This option is set in xorg.conf:

```

        Option      "VideoOverlay" "on"

```

Does anyone have any suggestions to speed this up?  Thanks

---

### Post by DouglasAWh on 2008-02-06
Just thought I should check back in and say that while I booted up the ubuntu partition yesterday to figure out using Synergy (which I did ubuntu-ubuntu, but I want to get Vista-ubuntu working), I have not had a chance to try out the dual monitors.  Perhaps tomorrow...I only am in the office Tuesday and Thursday.

---

### Post by jayach on 2008-02-06
FYI: I was able to restore performance by simply uninstalling the xserver-xgl package.

Also, if it helps anyone, I was never able to install fglrx the "ubuntu way" and get it to work.  I am running the standard 8.1 ati driver downloaded from their site.

---

### Post by DouglasAWh on 2008-02-29
Still no time to look at this.  We've been understaffed at work.  I do think everyone should vote this up though: [http://brainstorm.ubuntu.com/idea/322/](http://brainstorm.ubuntu.com/idea/322/)

---

### Post by DouglasAWh on 2008-05-07
We finally hired someone at work, which means I get a chance to look at this.  My video is HORRIBLE with 8.04.  Lots of lag and no desktop effects.  I did get the Catalyst Control Center to work though.  It seems to reset every time I reboot though.  

Catalyst says: 

driver is 8.47.3
Catalyst version 1.6
OpenGL is 1.4 (2.1 Mesa 7.0.3-rc2)


What other info would be helpful about the system.

Thanks so much for the help and sorry for checking out for so long!

EDIT: I do not have xserver-xgl installed according to apt.

---

### Post by danwood76 on 2008-05-07
Remove xserver-xgl and it will be better.

also it appears that your openGL vendor is incorrect.
Try reinstalling fglrx from synaptic.

---

### Post by DouglasAWh on 2008-05-07
> **danwood76 said:**
> Remove xserver-xgl and it will be better.

also it appears that your openGL vendor is incorrect.
Try reinstalling fglrx from synaptic.


I do not have xserver-xgl installed (at least according to apt).  Here's the proof

```

:~$ sudo apt-get remove xserver-xgl
[sudo] password for whitdoug: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xserver-xgl is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Perhaps I'm just confused on what is going on.

---

### Post by danwood76 on 2008-05-07
Sorry I misread your post.

The one problem you have is that the OpenGL vendor should be ATI with the fglrx drivers not mesa.
Try removing the drivers with the restricted driuvers manager, rebooting and then reinstalling with the restricted drivers manager.

---

### Post by DouglasAWh on 2008-05-07
ok, I'm not sure what is going on.  I just installed and uninstalled some fglrx stuff...not I get no GUI utility.  I'm loathe to restart to see if that fixes the lag, since before my settings have no held at a reboot.  Here's a screenshot of my synaptic: [http://www.flickr.com/photos/dawhitfield/2474081332/sizes/o/](http://www.flickr.com/photos/dawhitfield/2474081332/sizes/o/)

---

### Post by DouglasAWh on 2008-05-07
Does this help:

```

whitdoug@dev116:/usr/X11R6/bin$ dpkg -L fglrx-control
/.
/usr
/usr/bin
/usr/bin/amdcccle
/usr/share
/usr/share/applnk
/usr/share/applnk/amdcccle.kdelnk
/usr/share/applications
/usr/share/applications/apps
/usr/share/applications/apps/amdcccle.desktop
/usr/share/icons
/usr/share/icons/ccc_large.xpm
/usr/share/icons/ccc_small.xpm
/usr/share/pixmaps
/usr/share/ati
/usr/share/ati/amdcccle
/usr/share/ati/amdcccle/amdcccle_cs.qm
/usr/share/ati/amdcccle/amdcccle_da_DK.qm
/usr/share/ati/amdcccle/amdcccle_de.qm
/usr/share/ati/amdcccle/amdcccle_el_GR.qm
/usr/share/ati/amdcccle/amdcccle_es_ES.qm
/usr/share/ati/amdcccle/amdcccle_fi_FI.qm
/usr/share/ati/amdcccle/amdcccle_fr_FR.qm
/usr/share/ati/amdcccle/amdcccle_hu_HU.qm
/usr/share/ati/amdcccle/amdcccle_it_IT.qm
/usr/share/ati/amdcccle/amdcccle_ja.qm
/usr/share/ati/amdcccle/amdcccle_ko_KR.qm
/usr/share/ati/amdcccle/amdcccle_nl_NL.qm
/usr/share/ati/amdcccle/amdcccle_no.qm
/usr/share/ati/amdcccle/amdcccle_pl.qm
/usr/share/ati/amdcccle/amdcccle_pt_BR.qm
/usr/share/ati/amdcccle/amdcccle_ru_RU.qm
/usr/share/ati/amdcccle/amdcccle_sv_SE.qm
/usr/share/ati/amdcccle/amdcccle_th.qm
/usr/share/ati/amdcccle/amdcccle_tr_TR.qm
/usr/share/ati/amdcccle/amdcccle_zh_CN.qm
/usr/share/ati/amdcccle/amdcccle_zh_TW.qm
/usr/share/doc
/usr/share/doc/fglrx-control
/usr/share/doc/fglrx-control/copyright
/usr/share/doc/fglrx-control/changelog.Debian.gz

```

---

### Post by danwood76 on 2008-05-07
If you uninstall the drivers using the restricted drivers manager it should set your drivers back to the free drivers, or the vesa driver.
You can verify by after the uninstall checking what driver is selected in the /etc/xorg.conf file.

You need to reboot after uninstalling to unload the kernel modules.
Though this may not solve your problem its worth a shot.

Once back in ubuntu simply reinstall using the restricted drivers manager.

---

### Post by DouglasAWh on 2008-05-07
I click on System -> Administration -> Hardware Drivers and nothing happens.  How else would I go about figuring out what driver I am using?  I no longer have the ATI catalyst GUI.  Tx!

---

### Post by DouglasAWh on 2008-05-07
ok, I figured out how to find info:

```

whit6:~$ glxgears -info
GL_RENDERER   = Mesa GLX Indirect
GL_VERSION    = 1.4 (2.1 Mesa 7.0.3-rc2)
GL_VENDOR     = Mesa project: www.mesa3d.org
GL_EXTENSIONS = GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_object GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_paletted_texture GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_shared_texture_palette GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_APPLE_packed_pixels GL_ATI_draw_buffers GL_ATI_texture_env_combine3 GL_ATI_texture_mirror_once GL_ATIX_texture_env_combine3 GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_NV_blend_square GL_NV_fragment_program GL_NV_light_max_exponent GL_NV_point_sprite GL_NV_texgen_reflection GL_NV_texture_rectangle GL_NV_vertex_program GL_NV_vertex_program1_1 GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SGIX_shadow_ambient GL_SUN_multi_draw_arrays 


```

EDIT:
I'm confused, xorg.conf doesn't say anything about Mesa
```


# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
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
	Identifier   "DELL 1708FP"
	HorizSync    30.0 - 81.0
	VertRefresh  56.0 - 76.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc ATI Default Card"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc ATI Default Card"
	Monitor    "DELL 1708FP"
	DefaultDepth     24
	SubSection "Display"
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
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


```

---

### Post by DouglasAWh on 2008-05-12
> **DouglasAWh said:**
>  I no longer have the ATI catalyst GUI.

Actually, it just moved!  I still have it, and it still shows up as Mesa even though xorg says vesa.  Someone please help!

---

### Post by danwood76 on 2008-05-13
In your xorg.conf you are actually using the fglrx driver, mesa is just the OpenGL vendor, this is supposed to be ati if using the proprietry drivers.
The vesa driver is in an unused section.

You can uninstall the fglrx drivers using synaptic, searching for fglrx and uninstalling all the fglrx modules installed.

Then you might want to edit your xorg.conf to be this:
```

sudo gedit /etc/X11/xorg.conf

```
file contents:
```

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen      0  "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
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
	Identifier   "DELL 1708FP"
	HorizSync    30.0 - 81.0
	VertRefresh  56.0 - 76.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc ATI Default Card"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc ATI Default Card"
	Monitor    "DELL 1708FP"
	DefaultDepth     24
	SubSection "Display"
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```
I have removed all the proprietary driver references to allow the vesa driver to run.

---

### Post by DouglasAWh on 2008-05-13
so, yeah, no more lag, but I also don't have dual screens anymore, so um, can someone help me out with that again?  My xorg is as suggested above by danwood76.  I no longer have the ATI utility, at least in the two places it has been before.

---

### Post by DouglasAWh on 2008-05-13
> **danwood76 said:**
> Have you got the fglrx drivers installed correctly?
If so go into the catalyst control center and enable the second display and set it to extend the desktop.

Without these drivers you have no chance of enabling an extended desktop.

regards,
Danny

Ok, I just was going back through the posts and you seem to be contradicting yourself about what I should do.  Is there just no hope of this working smoothly with dual monitors?

---

### Post by danwood76 on 2008-05-13
Im not contradicting myself.
What I have told you to do is completely reinstall the drivers.

Remove the drivers with synaptuc (complete removal is probably best) reboot then reinstall the drivers using this guide:
For hardy:
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method)
For gutsy:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.4_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.4_Driver_Manually)

and finally to finish the install run this: (sets up the xorg.conf for you)
```

sudo aticonfig --initial -f

```

And when you reboot fglrx should be installed and working.
If you get any errors using the method above post them here.

---

### Post by DouglasAWh on 2008-05-13
It works.  Yay!  Now to figure out where they moved "solved" to.

---

### Post by shahnn28 on 2008-06-16
Help, I am new to Linux and setting up Extended desktop for a ATI Radeon 2400 Video Card. I see dual screens but not extended. HEre is a copy of my Xorg.conf. What am i doing wrong



 xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Main Screen"
    Screen        1  "Second Screen" Rightof "Main Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    Option        "Xinerama" "true"
EndSection

Section "Files"
EndSection

Section "Module"
    Load  "glx"
    Load  "GLcore"
    Load  "v4l"
EndSection

Section "InputDevice"
    Identifier  "Generic Keyboard"
    Driver      "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules" "xorg"
    Option        "XkbModel" "pc105"
    Option        "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier  "Configured Mouse"
    Driver      "mouse"
    Option        "CorePointer"
    Option        "Device" "/dev/input/mice"
    Option        "Protocol" "ImPS/2"
    Option        "ZAxisMapping" "4 5"
    Option        "Emulate3Buttons" "true"
EndSection

Section "Monitor"
    Identifier   "Main Monitor"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    HorizSync    28-51
    VertRefresh  43-60
EndSection

Section "Monitor"
    Identifier   "Second Monitor"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    HorizSync    28-51
    VertRefresh  43-60
EndSection

Section "Device"
    Identifier  "0 ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)"
    Driver      "ati"
    BusID        "PCI:1:0:0"
    Screen         0
EndSection

Section "Device"
    Identifier  "1 ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)"
    Driver      "ati"
    BusID        "PCI:1:0:0"
    Screen         1
EndSection

Section "Screen"
    Identifier "Main Screen"
    Device     "0 ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)"
    Monitor    "Main Monitor"
    DefaultDepth     24
    SubSection "Display"
        Depth     1
        Modes      "1024x768"
Section "Screen"
    Identifier "Second Screen"
    Device     "1 ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)"
    Monitor    "Second Monitor"
    DefaultDepth     24
    SubSection "Display"
        Depth     1
        Modes      "1024x768"
    EndSubSection
EndSection

---

### Post by danwood76 on 2008-06-18
Have you tried configuring dual screens with the catalyst control center?

---

