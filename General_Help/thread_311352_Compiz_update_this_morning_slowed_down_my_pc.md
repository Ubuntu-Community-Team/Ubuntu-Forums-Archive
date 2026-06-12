---
title: "Compiz update this morning slowed down my pc"
date: 2006-12-02
forum: General Help
---

### Post by Chrono86 on 2006-12-02
Hey guys~
Installed the Compiz (among other various updates that popped up) this morning. Anyways I restarted my computer and notice that any game that uses 3d acceleration has slowed down quite a bit. Plus, now I only have 2 desktops instead of 4. AND...haha...when I use ctrl-alt-(arrow key) the cube rotates REALLY FAST...what happened...and is there a way to revert or fix this?
Thanks
Adam

---

### Post by Chrono86 on 2006-12-02
Just wanted to give it a bump before it got lost :-?

---

### Post by Chrono86 on 2006-12-02
Nobody ran the update this morning and has had problems since? Well could somebody at least tell me how to revert the update?

---

### Post by Chrono86 on 2006-12-03
Well this got knocked down to page 5 already :-| ...

Anyways I noticed that when I run glxinfo | grep -i "vendor string" I get:

> server glx vendor string: SGI
client glx vendor string: NVIDIA Corporation
OpenGL vendor string: NVIDIA Corporation


What's with the SGI? Is that the problem?

And now when I run "glxinfo | grep" render I get:
> 
direct rendering: No
OpenGL renderer string: GeForce 6600 GT/PCI/SSE2/3DNOW!


What happened?

---

### Post by Chrono86 on 2006-12-03
Can nobody help me here? :(

---

### Post by Chrono86 on 2006-12-03
Maybe I'm just being rude, but within a few hours of me posting another message this thread just starts getting knocked back down the list where nobody will ever find it again...and I'm starting to get a little frustrated over the lack of replies...](*,)

---

### Post by anoir on 2006-12-03
I also have a problem after the recent update of compiz.

Compiz still seems to be working, but most of eye candies, such as cube-rotate, wobbly menus, and expose, are gone. Even with keyboard shortcuts defined in gconf-editor, I cannot rotate my desktop anymore. My guess is that the way to configure plug-ins is changed somehow.

I'm using compiz packages in Ubuntu repos and running nvidia binary driver on Quadro NVS 110M.

Because I'm extremely busy this month and using this laptop for serious research as well (okay, I know this is not recommended), I cannot afford time and resource to play with compiz right now, but I'm happy to see a solution here in forum.

P.S.
My understanding is that we should turn off compiz when we play games. I found wesnoth gets really slow with compiz, while it is not 3d game.

And I also find it interesting how this forum is supposed to work with so many posts that practically no one can catch up with. I happened to find this thread by searching with 'compiz update'.

---

### Post by Chrono86 on 2006-12-03
Yeah I have a nonXgl scrip I run if I want to turn compiz off to run certain games...but the problem is that makes the game window lack window borders so     and it won't let me drag the window around...does that happen to you too?

---

### Post by anoir on 2006-12-03
I just disable a start up script to run compiz

```

#!/bin/bash
gnome-window-decorator &  compiz --replace gconf &
```

on System->Preferences->Sessions and log into my system again.

---

### Post by Chrono86 on 2006-12-04
Since nobody has inputted much here...guess this will be my last post.

Here's what reported when I run glxinfo:

> name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_SGIX_fbconfig, 
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 6600 GT/PCI/SSE2/3DNOW!
OpenGL version string: 1.2 (2.1.0 NVIDIA 96.29)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_imaging, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_window_pos, GL_ARB_texture_non_power_of_two, GL_ARB_vertex_program, 
    GL_ARB_fragment_program, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_texture3D, GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, GL_EXT_texture_lod, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array, 
    GL_ATI_texture_mirror_once, GL_HP_occlusion_test, 
    GL_IBM_texture_mirrored_repeat, GL_NV_blend_square, 
    GL_NV_texgen_reflection, GL_NV_texture_rectangle, 
    GL_NV_texture_env_combine4, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, 
    GL_SGIX_depth_texture, GL_SGIX_shadow
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0 792358505 1647276659 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0 976302907 825245042 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0 892549937 809332066 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0 993079357 1768711726 Ncon


And here's what my xorg.conf looks like:

> Section "ServerLayout"
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
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA GeForce 6600GT"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA GeForce 6600GT"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1280x960" "1280x800" "1200x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1280x960" "1280x800" "1200x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1280x960" "1280x800" "1200x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1280x960" "1280x800" "1200x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1280x960" "1280x800" "1200x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1280x960" "1280x800" "1200x800" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection



---

### Post by anoir on 2006-12-05
At least you should be able to change the speed of rotation by modifying /apps/compiz/plugins/rotate/allscreens/options/flip_time to like 1000.

It seems that the default setting of compiz is different after the update. My problem that some feature are missing is solved by adding plugin names to /apps/compiz/general/allscreens/options/active_plugins manually.

---

