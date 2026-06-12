---
title: "Beryl + Aiglx + ATI + 6.10 = slow + error . . ."
date: 2006-12-17
forum: General Help
---

### Post by Patrick-Ruff on 2006-12-17
hey all, I recently realized that I can install beryl and make it work without XGL. so, here's what's going on now . . . it's really really sluggish and I get a weird libGL error.

I have a Mobility Radeon X300 PCIe. 

using the latest Beryl SVN's I think.

Beryl and Aiglx load, but everything is /very/ slow. XGL was atleast a couple times faster. 

heres what glxinfo gives . . .
```
patrick@eclypse:~$ glxinfo
name of display: :0.0
libGL warning: 3D driver claims to not support visual 0x4b
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R300 20060815 TCL
OpenGL version string: 1.3 Mesa 6.5.1
OpenGL extensions:
    GL_ARB_fragment_program, GL_ARB_imaging, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_MESAX_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_gpu_program_parameters, 
    GL_EXT_histogram, GL_EXT_packed_pixels, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program, 
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

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
0x4b 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

I tried this using the open source ati drivers that come with 6.10 out of the box.

heres my xorg.conf:
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"MaxTapTime"		"0"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. M22 [Radeon Mobility M300]"
	Driver		"ati"
	Option		"DRI"	"true"
	Option		"ColorTiling"	"on"
	Option		"EnablePageFlip"	"true"
	Option		"AccelMethod"	"EXA"
	Option		"XAANoOffscreenPixmaps"
	Option		"RenderAccel"	"true"
	#Option		"AGPMode" "x" <- x may be 1, 2, 3, 4, or 8 depending on your system.
	Option 		"AGPFastWrite" "on"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. M22 [Radeon Mobility M300]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```
if I have missed any info, please ask!


thanks to those who help.

---

### Post by x64Jimbo on 2006-12-17
fglrx should be used for 3D window manager enhancements. The open source driver is not up to the job.

---

### Post by Patrick-Ruff on 2006-12-17
umm, dude, I don't want to use XGL. you don't use FGLRX with aiglx. it does NOT work.

---

### Post by igknighted on 2006-12-17
The libGL error is normal.  Basically you cannot use rain effects, as the open source driver can't do them, but everything else should be OK.  To improve performance you could try upping your AGP bus speed if it doesn't crash (using "AGPMode" "4" for example) and also try switching "ati" as the driver name to "radeon".

---

### Post by Patrick-Ruff on 2006-12-17
I don't like it, this is ridiculous, it should be FASTER. not slower . . . really, this is really messed up . . . anyone have any more ideas?

---

### Post by Patrick-Ruff on 2006-12-17
also, I can't use the AGPMode, it just crashes X.

---

### Post by Patrick-Ruff on 2006-12-17
. . . hello?

---

### Post by x64Jimbo on 2006-12-17
Have some patience, man. This is a forum, not a chatroom. As for the solution, I'm sorry that my answer wasn't adequate.

---

### Post by Azakus on 2006-12-17
Open source drivers are not really good with 3d apps like Beryl. Try the proprietary drivers by changing the "driver" section of your xorg.conf from "ati" to "fglrx". Also install fglrx-control.

---

### Post by Patrick-Ruff on 2006-12-17
it's alright but I just formatted my system on the assumption that aiglx would work well with my card (and it damn well should . . . ) so I'm just a bit eager for an answer that'll work.

---

### Post by kvonb on 2006-12-17
I am using the opensource driver on Edgy and Beryl/3d apps work really well for me on the 9200se, and I don't even need to disable Beryl while playing 3d games.

I did drop my resolution down from 1600x1200 to 1400x1050 and it is fast enough.

Try adding: Option "TripleBuffer" "true" to xorg.conf and see if that makes a difference, and maybe rem out the AGPfastwrite line as well just to see.

There is also another option, something about using the PCI bus instead of the AGP, I can't remember where I read that though!

I've read that a lot of people are having problems with X300 cards, maybe search for X300 on the forums, it might spit something useful out.

---

### Post by Patrick-Ruff on 2006-12-17
dude, did you not just read what I said? **FGLRX is *inconpatable* with aiglx ** . . . unless something changed on me all of a sudden . . .

---

### Post by Azakus on 2006-12-17
> **kvonb said:**
> I am using the opensource driver on Edgy and Beryl/3d apps work really well for me on the 9200se, and I don't even need to disable Beryl while playing 3d games.

I did drop my resolution down from 1600x1200 to 1400x1050 and it is fast enough.

Try adding: Option "TripleBuffer" "true" to xorg.conf and see if that makes a difference, and maybe rem out the AGPfastwrite line as well just to see.

There is also another option, something about using the PCI bus instead of the AGP, I can't remember where I read that though!

I've read that a lot of people are having problems with X300 cards, maybe search for X300 on the forums, it might spit something useful out.

Whoops, my bad. I remember the opensource nvidia drivers are really crappy for 3D use (as in not supported at all), so that's my mistake. With it being a Mobility X300 though, I'm not so sure that the opensource drivers support it that well. The closed source drivers just started supporting it for Linux on January 18th, 2006 with version 8.21.7, so I'm not sure of full support.

---

### Post by Patrick-Ruff on 2006-12-17
could you possibly read into it ? I'm on dialup and I also am trying to learn C as well as do a bunch of stuff at once, so if someone would be kind enough to read into this for me I would greatly appriciate it.

---

### Post by Azakus on 2006-12-17
Try this [How To]("http://ubuntuforums.org/showthread.php?t=301364")

---

### Post by Patrick-Ruff on 2006-12-17
I'm not sure how exactly that will help me . . . isn't that just duplicating the same thing I did already? and the dude who wrote it was all like "and if it doesn't work cry"

meh.

---

### Post by Patrick-Ruff on 2006-12-17
ok umm, apparently all that link was for, was getting aiglx/beryl working in live cd, not in regular . . . what is the point of that?

---

### Post by kvonb on 2006-12-17
> ok umm, apparently all that link was for, was getting aiglx/beryl working in live cd, not in regular . . . what is the point of that?

The point is that if it works on the liveCD which includes the opensource driver then you can continue trying to get it working, if on the other hand it doesn't work then you can give up now saving yourself months of torment :rolleyes:.

---

### Post by Patrick-Ruff on 2006-12-17
umm, it WORKS. it just doesn't perform even close to as well as it did in XGL.

---

### Post by Patrick-Ruff on 2006-12-18
so, it seems that we had a huge misconception here. Beryl works, it's just 1.5x slower (or so.)  people keep telling me to use fglrx, but they obviously haven't read the actual thread. I don't want to use XGL, and XGL is required to use Beryl with FGLRX. 

  so, what must be done, we gotta figure out how to get it to perform as it should be . . . (yes we, if it were me alone I wouldn't be here, would I?)

---

### Post by Patrick-Ruff on 2006-12-18
well . . . I guess due to lack of replies, or actual answers that show I can get it working . . .  I guess I'm gonna be forced to use XGL again . . . *sighs* see, I read up on open source drivers and apparently they just straight up suck. and the really pathetic part is that, they are the only way I can get AIGLX running apparently.  Unless there is some other driver I don't know about that is capable of handling AIGLX, I guess I'm screwed.

---

### Post by Patrick-Ruff on 2006-12-18
so have we no suggestions? it seems like I'm talking to my self ;).  (though, I kind of am)

---

### Post by x64Jimbo on 2006-12-19
It would be a good idea to keep your ear to the ground about 3D advancements with ATI cards - I imagine that ATI's devs are scrambling to get fglrx to support AIGLX. They wouldn't want nVidia to have all the fun.

---

### Post by Patrick-Ruff on 2006-12-23
so far it doesn't appear that they give a rats *** about linux (excuse my french.)  I mean really, I would have thought they would have wanted it working a long time ago. I think they are just focusing on Vista right now . . . that's where their real money is . . .

---

### Post by CowzRule on 2006-12-29
I've ran Beryl on both XGL and AiGLX. I really saw no difference in overall speed of the effects. I did notice a difference in the smoothness of how the effects get displayed. XGL did a nicer job but only a little bit. It probably has more to do with the drivers than AiGLX or XGL.
I've been using the svn of Beryl since, I think, 0.1.1. It's been the updates to Beryl where I've noticed the speed improvments, so make sure you are up to date. The standard released version of Beryl in the repos is 0.1.4.
Currently I'm running svn ver. 0.1.5 with AiGLX. Here's the relevant section of my xorg.conf```
Section "Device"
	Identifier	"ATI Technologies, Inc. R420 JI [Radeon X800PRO]"
	Driver		"radeon"
	Option          "AGPMode" "8"
	Option          "ColorTiling" "on"	
	Option          "AccelMethod" "XAA"
	Option          "EnablePageFlip" "on"
	Option	   "XAANoOffScreenPixMaps"
	Option	   "RenderAccel" "true"
	BusID		"PCI:1:0:0"
EndSection
```I found that for my setup, only those options are needed. I tried the "AGPFastWrites On" option but it made X unable to load. The option "DRI true" was listed in /var/log/Xorg.0.log as causing a problem but I don't remember what.
The "AccelMethod XAA" option gives faster fps than EXA. See [this thread for more info on XAA and EXA.]("http://www.ubuntuforums.org/showpost.php?p=1424352&postcount=4")
Also be sure to add```
Section "Extensions"
  Option "Composite" "Enable"
EndSection
```to the very bottom of your xorg.conf file.
Hope it helps. :)

---

### Post by Patrick-Ruff on 2007-01-12
fglrx currently doesn't support aiglx, it doesn't work at all, to use aiglx the open source drivers must be used and they only have expiremental 3d accel for my particular card. 

aiglx is far more stable and a much better solution then xgl, everything works better. I'm not using xgl because of these issues.

---

### Post by Patrick-Ruff on 2007-01-27
anyone hear anything about ati adding support for this? or the open source drivers adding full 3d support?

---

### Post by x64Jimbo on 2007-01-30
I recently reinstalled Ubuntu on my laptop which has an ATI graphics card, and while I was at it, I decided to try and find a way to get Beryl on there. So I searched the forums and found an automated script that does all of it for you. Seriously, The whole install took about a minute and a half from the time I downloaded the script. Check out this thread:
[http://ubuntuforums.org/showthread.php?t=338771](http://ubuntuforums.org/showthread.php?t=338771)

---

### Post by Patrick-Ruff on 2007-01-30
that doesn't help. I don't have a problem with setting things up my self, I have a problem with how crappy the open-source acceleration is.  a script can't fix that, only a programmer can.

---

### Post by x64Jimbo on 2007-02-01
> **Patrick-Ruff said:**
> that doesn't help. I don't have a problem with setting things up my self, I have a problem with how crappy the open-source acceleration is.  a script can't fix that, only a programmer can.
The acceleration seems fine to me. It's even on a 3 year old laptop with shared video mem.

---

### Post by Rockfish42 on 2007-02-03
Depending on which graphics card you have you might need to disable some of the effects,
try disabling all of them and then adding them back on in turn.
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
Your card is listed as having experimental 3d support, that's probably the issue.
If you disable e.g. blur and trailfocus plugin does it help anything?
Alternatively you can try switching between the ati and radeon drivers to see which gives
better performance.
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu)
Lists some issues that might crop up.

---

### Post by igknighted on 2007-02-03
> **Patrick-Ruff said:**
> that doesn't help. I don't have a problem with setting things up my self, I have a problem with how crappy the open-source acceleration is.  a script can't fix that, only a programmer can.

Change your accel method from EXA to XAA, it works better with beryl.  It might make the performance usable.

---

### Post by Patrick-Ruff on 2007-02-04
I've tried that before, it did nothing.

it's the whole concept of using XGL, over all it takes away functionallity, it doesn't provide a good 2d acceleration layer, and it is just unstable and slow. 

my only hope is ATI releasing a GOOD driver for once or the open source drivers getting drastically better . . . (or I buy a new laptop . . . not likely in the next year.)

---

