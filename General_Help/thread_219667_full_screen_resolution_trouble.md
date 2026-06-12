---
title: "full screen resolution trouble"
date: 2006-07-20
forum: General Help
---

### Post by Dave54 on 2006-07-20
Not sure if this should be in hardware help.
My computer's display works fine up to 1600x1200 (65Hz). I run it at 1152x864 (85Hz). However, any games that run in full screen can not be put higher than 1024x768, or it closes or crashes. The only games I have so far to test this with are bzflag and neverball. Bzflag wants to open in fullscreen at 1600x1200. When opened, it immediately closes. Here's what I get in terminal:> dave@ubuntu:~$ bzflag
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  134 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x119
  Serial number of failed request:  122
  Current serial number in output stream:  124In order to successfully play bzflag, I use "bzflag -window", then change the resolution to 1024x768 and it goes to fullscreen.
I have an nVidia NV34 [GeForce FX 5200] card. As for the driver, I used method 1 [here]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper").

Any help is much appreciated.
Please tell me if there's any more information I should post.

---

### Post by Dave54 on 2006-07-20
Since I haven't had any replies in three hours, I'll update with all the information I have.

If I run Neverball in terminal, I get an error message, but it continues to run. when I change the resolution from 1042x768 to 1280x1024, it shuts down and leaves me zoomed in on my desktop. Pushing the mouse on the sides of the screen pans the screen so I can see the rest of the desktop. To fix this, I go to System > Preferences > Screen resolution, and click apply. Here's what's left in terminal:> dave@ubuntu:~$ neverball
open /dev/sequencer: No such file or directory
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  134 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x119
  Serial number of failed request:  146
  Current serial number in output stream:  148 The "open /dev/sequencer: No such file or directory" line is the error I get when opening.

I have downloaded and installed Enemy Territory. It runs fine, but when I quit, it always leaves me zoomed in on the desktop, and this one doesn't go away unless I log out and in. When I put the resolution too high in ET, it doesn't quit but rather shows a large and skewed display.

Here is what the terminal showed after I opened ET, changed the resolution to 1280x1024, changed it back, and quit. (I highlighted anything that seems like errors.)

```
dave@ubuntu:~$ et
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/dave/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
[COLOR="Red"]couldn't exec language.cfg[/COLOR]
execing profiles/Dave54/etconfig.cfg
[COLOR="Red"]couldn't exec autoexec.cfg[/COLOR]
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce FX 5200/AGP/SSE2
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_NV_fog_distance
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
...using GLX_SGI_swap_control
...using GLX_SGI_video_sync
XF86 Gamma extension initialized

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce FX 5200/AGP/SSE2
GL_VERSION: 2.0.2 NVIDIA 87.62
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_object GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_paletted_texture GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_shared_texture_palette GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_timer_query GL_EXT_vertex_array GL_HP_occlusion_test GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum
GLX_EXTENSIONS: GLX_EXT_visual_info GLX_EXT_visual_rating GLX_SGIX_fbconfig GLX_SGIX_pbuffer GLX_SGI_video_sync GLX_SGI_swap_control GLX_ARB_multisample GLX_NV_float_buffer GLX_ARB_get_proc_address
GL_MAX_TEXTURE_SIZE: 4096
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU:
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 32
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: enabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------
------------------------------------
----- Sound Info -----
sound system is muted
    1 stereo
32768 samples
   16 samplebits
    1 submission_chunk
22050 speed
0x0xb00ba000 dma buffer
No background file.
----------------------
Sound memory manager started
Sys_LoadDll(/home/dave/.etwolf/etmain/ui.mp.i386.so)...
[COLOR="Red"]Sys_LoadDll(/home/dave/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/dave/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"[/COLOR]
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xae528f40
Sys_LoadDll(ui) succeeded!
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: localhost
Alias: ubuntu
IP: 127.0.0.1
Started tty console (use +set ttycon 0 to disable)
^5PunkBuster Client: PunkBuster Client (v1.152 | A0) Enabled
^5PunkBuster Client: Game Version [ET 2.60 linux-i386 Mar 10 2005]
^5PunkBuster Client: Not Connected to a Server
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
RE_Shutdown( 1 )
[COLOR="Red"]X Error of failed request: BadValue (integer parameter out of range for operation)
  Major opcode of failed request: 134
  Minor opcode of failed request: 10
  Serial number of failed request: 289[/COLOR]
Hunk_Clear: reset the hunk ok
----- Initializing Renderer ----
-------------------------------
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 8: 1280 1024
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 1280x1024
[COLOR="Red"]X Error of failed request: BadValue (integer parameter out of range for operation)
  Major opcode of failed request: 134
  Minor opcode of failed request: 10
  Serial number of failed request: 18[/COLOR]
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce FX 5200/AGP/SSE2
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_NV_fog_distance
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
...using GLX_SGI_swap_control
...using GLX_SGI_video_sync
XF86 Gamma extension initialized

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce FX 5200/AGP/SSE2
GL_VERSION: 2.0.2 NVIDIA 87.62
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_object GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_paletted_texture GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_shared_texture_palette GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_timer_query GL_EXT_vertex_array GL_HP_occlusion_test GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum
GLX_EXTENSIONS: GLX_EXT_visual_info GLX_EXT_visual_rating GLX_SGIX_fbconfig GLX_SGIX_pbuffer GLX_SGI_video_sync GLX_SGI_swap_control GLX_ARB_multisample GLX_NV_float_buffer GLX_ARB_get_proc_address
GL_MAX_TEXTURE_SIZE: 4096
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 8, 1280 x 1024 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU:
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 32
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: enabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----
Sys_LoadDll(/home/dave/.etwolf/etmain/ui.mp.i386.so)...
[COLOR="Red"]Sys_LoadDll(/home/dave/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/dave/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"[/COLOR]
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xae528f40
Sys_LoadDll(ui) succeeded!
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
RE_Shutdown( 1 )
[COLOR="Red"]X Error of failed request: BadValue (integer parameter out of range for operation)
  Major opcode of failed request: 134
  Minor opcode of failed request: 10
  Serial number of failed request: 288[/COLOR]
Hunk_Clear: reset the hunk ok
----- Initializing Renderer ----
-------------------------------
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce FX 5200/AGP/SSE2
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_NV_fog_distance
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
...using GLX_SGI_swap_control
...using GLX_SGI_video_sync
XF86 Gamma extension initialized

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce FX 5200/AGP/SSE2
GL_VERSION: 2.0.2 NVIDIA 87.62
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_object GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_paletted_texture GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_shared_texture_palette GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_timer_query GL_EXT_vertex_array GL_HP_occlusion_test GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum
GLX_EXTENSIONS: GLX_EXT_visual_info GLX_EXT_visual_rating GLX_SGIX_fbconfig GLX_SGIX_pbuffer GLX_SGI_video_sync GLX_SGI_swap_control GLX_ARB_multisample GLX_NV_float_buffer GLX_ARB_get_proc_address
GL_MAX_TEXTURE_SIZE: 4096
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU:
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 32
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: enabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----
Sys_LoadDll(/home/dave/.etwolf/etmain/ui.mp.i386.so)...
[COLOR="Red"]Sys_LoadDll(/home/dave/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/dave/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"[/COLOR]
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xae528f40
Sys_LoadDll(ui) succeeded!
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
----- CL_Shutdown -----
RE_Shutdown( 1 )
[COLOR="Red"]X Error of failed request: BadValue (integer parameter out of range for operation)
  Major opcode of failed request: 134
  Minor opcode of failed request: 10
  Serial number of failed request: 288[/COLOR]
-----------------------
----- CL_Shutdown -----
-----------------------
Shutdown tty console
```

Well, that's all I got.
If you think you know what the problem is, please tell me.
Thank-you.

---

### Post by Dave54 on 2006-07-20
I've done a lot of research and have found that many people have had this problem. While a few have found work-arounds, none have solved the problem.
The best work-around I've found is to "edit the xorg.conf" file to limit the abilities of the monitor. However, one can't use higher resolutions with this fix, which is exactly my problem.
I have found this problem (online) across most linux distros, but here's some that were posted on the ubuntu forums:
[http://www.ubuntuforums.org/showthread.php?t=75465]("http://www.ubuntuforums.org/showthread.php?t=75465")
[http://www.ubuntuforums.org/showthread.php?t=24359]("http://www.ubuntuforums.org/showthread.php?t=24359")
[http://www.ubuntuforums.org/showthread.php?t=19907]("http://www.ubuntuforums.org/showthread.php?t=19907")
[http://www.ubuntuforums.org/showthread.php?t=187576]("http://www.ubuntuforums.org/showthread.php?t=187576")
[http://www.ubuntuforums.org/showthread.php?t=190741]("http://www.ubuntuforums.org/showthread.php?t=190741")
[http://www.ubuntuforums.org/showthread.php?t=47196]("http://www.ubuntuforums.org/showthread.php?t=47196")

I will continue researching to see if anyone has ever found a solution to this problem. Any advice will be much appreciated.

---

### Post by Dave54 on 2006-07-21
YES! I figured it out! But I still need help.

The problem is that my current resolution is 1152x864 @85Hz. My monitor can't display anything higher and still be at 85Hz. I realized this was the problem when I went on my Windows box, opened BZflag, and went to Change Video Format. It had about 30 choices: different resolutions at different **refresh rates.**

Edit: clarification: On Bzflag on Ubuntu, there's choices for different screen resolutions, but not for different refresh rates.

So for some reason, when Linux games try to change the screen resolution, they don't change the refresh rate (for me).

If I go to System > Preferences > Screen Resolution, I can't change the refresh rate. Each resolution has only one refresh rate allowed. However, if I choose 1600x1200, the refresh rate goes to 65Hz. If I choose this setting and open BZflag, I can then choose **any** screen resolution without error (I assume because all screen resolutions are compatible with 65 Hz).

So, now that I have identified the problem, can anyone help with a solution? Are there screen resolution tools that will allow me to customize (lower) my refresh rate for any resolution? Is there any way to make the games automatically adjust the refresh rate? Do I need some sort of Monitor driver?

As always, any help is much appreciated.

---

### Post by Dave54 on 2006-07-22
Ok, My screen resolutions are:

1600x1200 @ 65 Hz
1280x1024 @ 75 Hz
1152x864 @ 85 Hz
1024x768 @ 85 Hz
832x624 @ 75 Hz
800x600 @ 85 Hz
640x480 @ 85 Hz

When my desktop is at 85 Hz, no full screen game can go above 1152x864. I need confirmation that **anyone** can play a full screen game at a higher resolution when their desktop is at the max Hz.

Steps to do this:
1. Go to System > Preferences > Screen Resolution
2. Select each of the resolutions to find out you max refresh rate
3. Select and apply your highest screen resolution at your max refresh rate (mine would be 1152x864 @ 85 Hz)
4. Open a fullscreen game (Like BZflag, Enemy-Territory, Alien Arena, or Neverball) and use the in-game options to change the screen resolution to something higher than your desktop setting
5. Report your findings here.

Thank-you for helping me out with this.

---

### Post by RJARRRPCGP on 2006-07-22
> **Dave54 said:**
> 
When my desktop is at 85 Hz, no full screen game can go above 1152x864. 

It's probably a monitor limitation. You're probably required to get another monitor if you want 85 hz and higher with the resolution higher than 1152x864. Sorry. :(

---

### Post by Dave54 on 2006-07-22
> **RJARRRPCGP said:**
> It's probably a monitor limitation. You're probably required to get another monitor if you want 85 hz and higher with the resolution higher than 1152x864. Sorry. :(

Thanks for the post.

I know that my monitor is unable to display 85 Hz and higher with the resolution higher than 1152x864. However, when I run a full screen game with the resolution higher than 1152x864, **it should lower the refresh rate** so my monitor can display it, shouldn't it? This is why I need someone to confirm that a game will normally do this.

---

### Post by qrm on 2006-08-08
im having the same error, im running ET at r_mode 4(that is 800x400) and after exiting the game it doesnt change back to my normal resolution, which is 1280x1024

---

### Post by Dave54 on 2006-08-09
Well, I found a very interesting "solution".

I'm running compriz/xgl. Now when I play a full screen game, it plays in the resolution (and refresh rate) of my desktop. Changing the resolution in the game to a smaller resolution provides a smaller screen with a black border, allowing my screen to stay at the same resolution. In case you're not familiar, compriz/xgl is that thing famous for projecting your desktop on a cube.

If you want to try out compriz/xgl on Dapper, it's pretty easy. I recommend using [http://www.ubuntuforums.org/showthread.php?t=222034]("http://www.ubuntuforums.org/showthread.php?t=222034") for installation. Keep in mind you may use Synaptic Package Manager instead of apt-get.

There might be a fix to the problems compriz/xgl has with full screen games.

---

