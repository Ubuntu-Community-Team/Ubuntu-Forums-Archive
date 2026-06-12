---
title: "What could cause failsafe terminal to fail?"
date: 2007-02-26
forum: General Help
---

### Post by Moses on 2007-02-26
I'm running Ubuntu Ultimate 1.1. I have little idea what could cause this, but no matter what session I choose at login, I get bounced back to the login screen about 5 seconds later. 

The last thing I did before logging out for the last time was adding Skype as a startup program in the session manager. (I also added another program, but I can't remember what, at the moment). 

Is this the likely culprit? If so how do I remove these items once booted into recovery mode?

---

### Post by bodhi.zazen on 2007-02-26
An error message would help.

boot Ubuntu, open a terminal, change to tty1 with the key combination Ctrl-Alt-F1

Then enter : ```
sudo /etc/init.d/gdm stop
startx
```

Post any error messages ;)

---

### Post by Moses on 2007-02-26
Thanks, I will try that shortly.

Unfortunately, I haven't got any error message ;). I just get a blue screen with the cursor for a few seconds then a blank screen followed by the login prompt again.

---

### Post by Moses on 2007-02-26
Okay I tried switching to tty1. :confused: This graphically corrupted the entire screen, so I couldn't try the next step. 

I'm started to think this is a graphics card related problem. For the record I have an ATI X800Pro with flgrx.

I had recently created an Xgl session that also ran beryl-manager. Beryl seemed to be working correctly, but I did notice problems just before logging off: all my visual effects were spontaneously reset to default, and changing them had no effect, they remained at the default. This is what actually prompted me to log off, since then I haven't been able to get back on.

---

### Post by Moses on 2007-02-26
bodhi.zazen? Any further advice?

I'm made several attempts to ditch XP in the past, but I always come up with something like this which makes me switch back. *sigh*

---

### Post by bodhi.zazen on 2007-02-26
> **Moses said:**
> bodhi.zazen? Any further advice?

I'm made several attempts to ditch XP in the past, but I always come up with something like this which makes me switch back. *sigh*

LOL ~ would hate to lose you to $M :(

I recall having more then my share difficulty with $M, like the time my antiviral software recognized "Explorer" (NOT IE) as a virus and removed it .... LOL

Well, it looks like a problem with your video driver ...

And I am not so good with ATI, but since no one else has piped in I will try ...

Boot to recovery mode and either restore /etc/X11/xorg.conf from back up. You did back up xorg.conf didn't you ???

If not type this in a terminal:

```
ls /etc/X11 | grep xorg
``` to see if an automatic back up was made for you ...

To restore, ```
cp /etc/X11/xorg.conf.back_up_file /etc/X11/xorg.conf
```

Re boot and see it that does the trick ...

If not, 

Again boot to recovery mode, and try

```
dpkg-reconfigure -phigh xserver-xorg
```

And again re-boot ...


If that fails, boot to recovery mode and try re-installing your ATI driver, with the envy script :

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

From CLI:
```
	wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.7.5-0ubuntu1_all.deb
sudo dpkg -i envy_0.7.5-0ubuntu1_all.deb
```

then follow directions from the site ....





Now if that fails, :(

---

### Post by Moses on 2007-02-27
I spent an entire day trying several guides on how to get beryl working, as a result I have an abundance of xorg.conf backups. However, I tried several, including what I believe was the original, but they didn't work. :(  I also tried dpkg-reconfigure etc... but that didn't help either. 

The wget command presented me with a 'connection failed' so I am going to download the file now in XP and try install it later.


Were my previous suggestions that a startup program might be causing this problem erroneous? Is it not worth pursuing?

Another thing that comes to mind is the fact that I only allocated around 5 gigs for the partition. After installing Ultimate, I only had ~200mb left. Could this in anyway be interfering with the login process? I'm getting desperate. :D

---

### Post by bodhi.zazen on 2007-02-27
> **Moses said:**
> I spent an entire day trying several guides on how to get beryl working, as a result I have an abundance of xorg.conf backups. However, I tried several, including what I believe was the original, but they didn't work. :(  I also tried dpkg-reconfigure etc... but that didn't help either. 

The wget command presented me with a 'connection failed' so I am going to download the file now in XP and try install it later.


Were my previous suggestions that a startup program might be causing this problem erroneous? Is it not worth pursuing?

Another thing that comes to mind is the fact that I only allocated around 5 gigs for the partition. After installing Ultimate, I only had ~200mb left. Could this in anyway be interfering with the login process? I'm getting desperate. :D

LOL

To be honest, without an error message it is all just a guess ...

The idea that the disk is too full is a good one.

You may be able to boot to the live CD and either resize (enlarge) the partition or delete/move/back up some stuff to make some free space, then re-boot ...

It the problem is not with xorg.conf, well I hope you have a back up of the copy that was working with beryl ;)

HTH

---

### Post by Moses on 2007-02-27
Hehe, I do have backup... but once I get this other mess sorted out, I'd like to address that, because I'm not convinced it was working perfectly.

Anyway, I since tried the envy script, but I could only run it from recovery mode. It only gave me the option to install/uninstall nVidia drivers. :( 

Do you think the free space issue is a possibility? Does anyone have any experience with this?

And finally, Do you know of any large apps in Ultimate that are good candidates for removal? 

I've heard horror stories about resizing partitions after installing linux, so I don't won't to go down that road yet. ;)

---

### Post by Moses on 2007-02-27
Good news. I deleted the game 'legends' and I can now login :)

Should I post my beryl question here, or start a new thread?

---

### Post by bodhi.zazen on 2007-02-27
If you like, post here and we will see if we can help.

If not, starting a new thread makes sense ...

---

### Post by Moses on 2007-02-27
I finally got everything else working.... now onto beryl.

I have created an xgl session by following some guide. beryl does then work, but it is a little slow. I have noticed when I wobble a window around my CPU usage jumps to 50%. (P4 3.0Ghz, 1Gb DDR4 AGP X800Pro)

A friend of mine tells me that the "server glx vendor string: SGI" indicates that my glx is running in software :(

direct rendering is 'yes' but if I run glxinfo from the xgl session, it is actually 'no'. 

How do I fix this? (easily :D) 

PS: envy doesn't seem to work, it only gives me the option to install/uninstall nVidia drivers. 


glxinfo:
```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
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
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 PRO Generic
OpenGL version string: 2.0.6174 (8.31.5)
OpenGL extensions:
    GL_ARB_multitexture, GL_EXT_texture_env_add, GL_EXT_compiled_vertex_array, 
    GL_S3_s3tc, GL_ARB_depth_texture, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_multisample, GL_ARB_occlusion_query, GL_ARB_point_parameters, 
    GL_ARB_point_sprite, GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_blend, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_ARB_draw_buffers, GL_ATI_draw_buffers, 
    GL_ATI_element_array, GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, 
    GL_ATI_map_object_buffer, GL_ATI_separate_stencil, 
    GL_ATI_texture_compression_3dc, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_float, GL_ATI_texture_mirror_once, 
    GL_ATI_vertex_array_object, GL_ATI_vertex_attrib_array_object, 
    GL_ATI_vertex_streams, GL_ATIX_texture_env_combine3, 
    GL_ATIX_texture_env_route, GL_ATIX_vertex_shader_output_point_size, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_texgen_reflection, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_EXT_vertex_shader, GL_HP_occlusion_test, GL_NV_blend_square, 
    GL_NV_occlusion_query, GL_NV_texgen_reflection, GL_SGI_color_matrix, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x37 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x39 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x41 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x43 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x44 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x45 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x46 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x47 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x48 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x49 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x4a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x52 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x62 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None

```

---

