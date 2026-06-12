---
title: "Beryl Crash (With Pasteinfo)"
date: 2007-05-29
forum: General Help
---

### Post by cydec on 2007-05-29
_This is what i got:_

```
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : failed

Support for non power of two textures missing
beryl: Support for non power of two textures missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0
```

Does anybody know what to do here? Or got the same problem as me?
I'm beginning to think that beryl won't work without ATI or Nvidia stuff.

_My Graphics card:_

> Section "Device"
	Identifier	"S3 Inc. VT8375 [ProSavage8 KM266/KL266]"
	Driver		"savage"
	BusID		"PCI:1:0:0"
EndSection

---

### Post by cydec on 2007-05-30
Beginning to think that it's realy a problem with my Graphics Cards.
Is there any Graca genius around here who could find out what the exact cause could be?] :(

I've been searching the Forums but found really nothing related... Sorry this really wasn't meant as a bump, seems that i'm not the only one having the problem but most of time they aren't completely related to my dcase.

---

### Post by cydec on 2007-05-31
Got some new information. Got some information when i started a command in my console. 

```
xxxxx@T-Laptop:~$ beryl-manager --no-force-window-manager
xxxxx@T-Laptop:~$ /usr/bin/compiz.real: GLX_EXT_texture_from_pixmap
 is not supported by direct rendering context, trying indirect rendering context instead
Segmentation fault (core dumped)

```

---

### Post by Kuoi on 2007-05-31
Type in terminal :
> compiz --replace --indirect-rendering gconf

Hope this helps , Kuoi

---

### Post by cydec on 2007-05-31
Oh yeah just to be sure here is my glxinfo:

```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_visual_select_group
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_visual_select_group
OpenGL vendor string: S3 Graphics Inc.
OpenGL renderer string: Mesa DRI ProSavageDDR 20061110 AGP 1x x86/MMX/SSE2
OpenGL version string: 1.2 Mesa 6.5.2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_texture_compression, GL_ARB_texture_env_add, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_transpose_matrix, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_histogram, GL_EXT_packed_pixels, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_lod_bias, GL_EXT_texture_object, 
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_MESA_window_pos, 
    GL_NV_light_max_exponent, GL_NV_texgen_reflection, GL_OES_read_format, 
    GL_SGI_color_matrix, GL_SGI_color_table, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x22 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x23 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x24 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x25 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x26 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x27 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x28 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x29 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x42 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

---

### Post by cydec on 2007-05-31
> **Kuoi said:**
> Type in terminal :
> compiz --replace --indirect-rendering gconf

That command totally crashed my X. even CTRL-Alt-Backspace wouldn't restart my X.
Totally froze everything up, But thanks for trying, I was waiting a long time for someone to reply...

---

### Post by Kuoi on 2007-05-31
Sorry about that , and I've found this on the Compiz site , maybe this helps ?

>  How can I get Compiz to start properly on my integrated Intel Graphics Chipset (i810-i950) with AIGLX

Using "compiz --replace gconf/ini&" on an Intel graphics chip will probably yield this

"compiz:GLX_EXT_texture_from_pixmap is not supported by direct rendering context, trying indirect rending instead

compiz:GLX_EXT_texture_from_pixmap not found

compiz:Failed to manage Screen :0

compiz:No managable screens on Display 0:0"


You will need to launch compiz like this : "LIBGL_ALWAYS_INDIRECT=TRUE compiz --replace gconf/ini&" 

Kuoi

---

### Post by cydec on 2007-06-01
> **Kuoi said:**
> Sorry about that , and I've found this on the Compiz site , maybe this helps ?

> How can I get Compiz to start properly on my integrated Intel Graphics Chipset (i810-i950) with AIGLX
Using "compiz --replace gconf/ini&" on an Intel graphics chip will probably yield this
"compiz:GLX_EXT_texture_from_pixmap is not supported by direct rendering context, trying indirect rending instead
compiz:GLX_EXT_texture_from_pixmap not found
compiz:Failed to manage Screen :0
compiz:No managable screens on Display 0:0"

You will need to launch compiz like this : "LIBGL_ALWAYS_INDIRECT=TRUE compiz --replace gconf/ini&"

Kuoi


Still nothing here mate, thanks for still trying!
I'm searching as a mad man atm, almost giving up hope.

```
$ /usr/bin/compiz.real: Support for non power of two textures missing
$ /usr/bin/compiz.real: Failed to manage screen: 0
$ /usr/bin/compiz.real: No manageable screens found on display :0.0
```

---

### Post by Kuoi on 2007-06-01
Type in terminal

> gksudo gedit /etc/X11/xorg.conf
Ad this to the section "screen"

> Option "AddARGBGLXVisuals" "True"
so it looks like this ... but remember this is mine , yours will be a bit different

> Section "Screen"
Identifier "Default Screen"
Device "Nvidia Geforce 4"
Monitor "Generic Monitor"
DefaultDepth 24
[COLOR="Red"]Option "AddARGBGLXVisuals" "True"[/COLOR]
And now ad this line at the very end of the file ...

> Section "Extensions"
Option "Composite" "Enable"
EndSection
Hope this helps , Kuoi

---

