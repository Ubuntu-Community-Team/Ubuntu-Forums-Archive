---
title: "Screen Turns White When I Enable Desktop Effects"
date: 2007-05-28
forum: General Help
---

### Post by kimcheefreak17 on 2007-05-28
Hi, I'm sure you get this a lot, but here it goes. I'm new to Ubuntu and I wanted to get the fancy eye candy I see all over the place for Ubuntu. So, here's my problem.

When I go to Desktop Effects and press "Enable Desktop Effects", the screen turns white, completely white. I can still see the cursor, though. I have no clue what's going on. I also tried getting Beryl and successfully made it through all the steps I was instructed to, but when I typed "beryl-manager" into the terminal, the screen turned white too, just like it did when I tried enabling the desktop effects.

Oh, also, I'm using an ATI Radeon 9600.

Any help would be appreciated. Thanks!

---

### Post by Crafty Kisses on 2007-05-28
It sounds like you need to install your drivers. Go download the appropiate packages from the Synaptic Packet Manager, and that after that:

In the console type:

```
ati-driver-installer-8.34.8-x86.x86_64.run
```

Make sure you backup your xorg.conf file before you install the driver.

Go into console and type:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-old
```

---

### Post by kimcheefreak17 on 2007-05-28
I'm not entirely sure on which things to install, I went to ATI's website and got the latest version of the driver installer,  ATI Proprietary Linux x86 Display Driver 8.36.5 . I followed the directions on how to launch it, but it wouldn't launch. I put in  *sh ./ati-driver-installer-8.36.5.run*, but terminal said it couldn't open it. Then I put in *sh ati-driver-installer-8.36.5-x86.x86_64.run*, the actual name of the file, but that didn't work either. It gave me this message: 

Detected configuration:
Architecture: i686 (32-bit)
X Server: X.Org 7.2.x

Detected version of X does not have a matching 'x720' directory
You may override the detected version using the following syntax:
     X_VERSION=<xdir> ./ati-driver-installer-<ver>-<arch>.run [--install]

The following values may be used for <xdir>:
    x430        XFree86 4.3.x
    x430_64a    XFree86 4.3.x 64-bit
    x680        X.Org 6.8.x
    x680_64a    X.Org 6.8.x 64-bit
    x690        X.Org 6.9.x
    x690_64a    X.Org 6.9.x 64-bit
    x700        X.Org 7.0.x
    x700_64a    X.Org 7.0.x 64-bit
    x710        X.Org 7.1.x
    x710_64a    X.Org 7.1.x 64-bit
Removing temporary directory: fglrx-install.Uj6902

I was then advised to go to System-> Administration -> Restricted Drivers Manager and try it from there. I did that and it helped, a bit... Now when I try to enable Desktop Effects, instead of getting a white screen, it just tells me I can't do it. I don't understand, I thought my graphics card could handle this.

Thanks in advance.

---

### Post by Ozeuss on 2007-05-28
Um... just a thought, it might sound silly- have you restarted X since? or tried to restart the computer?
i got i white screen a few weeks ago (after a while of compiz and beryl running), and a computer restart solved it. windowz like solution, i know- but no trace of it ever since.

---

### Post by kimcheefreak17 on 2007-05-28
Yeah... I have tried restarting the computer, but to no avail. :( I've even tried reinstalling Ubuntu.:(
Thanks though.

---

### Post by sectionEight on 2007-05-29
My screen turns white when I turn on the Desktop Effects as well. But when I reboot it just goes back to the white screen.

I can log in using a gnome failsafe session but is there any way to turn the desktop effects off? Is there a setting somewhere in my home directory? I have had a look but I can't find anything.

Thanks.

---

### Post by sectionEight on 2007-05-29
Please ignore my previous post. I got a bit trigger happy (I had been looking for a solution with no luck but found one about two minutes after posting!! D'oh!!!).

Just for reference here is the solution I found:

If you want to turn off desktop effects from the command line, I am assuming you cannot see anything on your desktop, you may have a white or black screen.
First, restart by pressing CTRL- left ALT-Backspace
You will see a login screen.
before logging in, click the button for options at the lower right
then click change session
You may have gotten this far already, but perhaps another reader is having the same problem, so,
Select failsafe terminal
now login
at the prompt type:
gconf-editor
this will open up the registry
now select Desktop->Gnome->Applications->window_manager
the current and default key values will probably say /usr/bin/compiz
select the key value by clicking once on the key value
you can completely erase both the default and current values and when ubuntu restarts it will automatically fill in these vaules with /usr/bin/metacity
You can alternatively enter in /usr/bin/metacity for [b]both[b] the current and default values.
Now restart (Ctrl_left Alt-Backspace) and at the login screen change your session back to xclient and login.

everything's back to normal (if you left the key values blank, it will take a second for everything to appear normal)
hope this helps

---

### Post by Crafty Kisses on 2007-05-29
> **kimcheefreak17 said:**
> Hi, I'm sure you get this a lot, but here it goes. I'm new to Ubuntu and I wanted to get the fancy eye candy I see all over the place for Ubuntu. So, here's my problem.

When I go to Desktop Effects and press "Enable Desktop Effects", the screen turns white, completely white. I can still see the cursor, though. I have no clue what's going on. I also tried getting Beryl and successfully made it through all the steps I was instructed to, but when I typed "beryl-manager" into the terminal, the screen turned white too, just like it did when I tried enabling the desktop effects.

Oh, also, I'm using an ATI Radeon 9600.

Any help would be appreciated. Thanks!

Also can you post your glx info, simply go in the terminal and type:
```
glxinfo
```

---

### Post by kimcheefreak17 on 2007-05-29
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
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_program, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_shared_texture_palette, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_fragment_program, GL_NV_light_max_exponent, GL_NV_point_sprite, 
    GL_NV_texgen_reflection, GL_NV_texture_rectangle, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

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
0x43 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

Right now, I'd just like to thank everyone for their help. I'm sorry if I need someone to hold my hand as I get a hold on Ubuntu, but its sort of overwhelming moving over from Windows. :D

---

### Post by IceMatrix8 on 2007-06-02
i also have the same problem in 2 computers actually...when i enable the effects my screen goes blank!
the only common thing between them is that i run ubuntu from cd...
the desktop pc has a ATI X series and my laptop has an SiS 661FX display adapter and both turn white when enabling effects...
will my problem be solved if i install ubuntu and then install the correct drivers? and even if i do these two things and i still get the blank screen will be there another solution??
Will this FIX solve my problem?----> [http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

p.s. thanx for your time,sorry for my bad english(greek guy;))

---

