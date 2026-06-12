---
title: "Ubuntu 16.04 becomes slow and I can't tell why"
date: 2018-03-07
forum: General Help
---

### Post by carega on 2018-03-07
Hello guys,

I'm wondering if anyone could help me. I've been running ubuntu 16.04 for a while and ever since I upgraded after a while using it the computer suddenly becomes slow. I go and check the system monitor and it doesn't show any specific app doing a lot of work but it does show this:

[ATTACH=CONFIG]278839[/ATTACH]

That CPU 2 is doing a whole lot of work by itself.

I tried troubleshooting myself, thinking it might be something related with the internet (though not download/upload changes are shown in the graphs). It kinda worked as "CPU 2" relaxed:

[ATTACH=CONFIG]278840[/ATTACH]

But I don't think the problem is related with a process connecting to the Internet or something since it doesn't work all the time:

[ATTACH=CONFIG]278841[/ATTACH]

So can anyone help me to see how can I found out who the culprit is? Maybe it's related to my graphics card? I don't know, I'm just thinking out loud.

Thanks!!

---

### Post by TheFu on 2018-03-07
Please post the output from **top** to start within _code tags_. Text only please.  Images aren't that useful and eat bandwidth for people who pay for internet by the byte.

* free -hm 
* iostat
* vmstat
would be helpful too, but top is where I'd start.

---

### Post by carega on 2018-03-07
Thank you for replying! As per requested:

top:

```
top - 19:45:31 up  3:54,  1 user,  load average: 2,75, 3,71, 3,01
Tareas: 214 total,   2 ejecutar,  212 hibernar,    0 detener,    0 zombie
%Cpu(s): 23,7 usuario,  5,4 sist,  0,0 adecuado, 70,8 inact,  0,0 en espera,  0,
KiB Mem :  3937124 total,   569596 free,  2319628 used,  1047900 buff/cache
KiB Swap:  4090876 total,  4064496 free,    26380 used.   971348 avail Mem 

  PID USUARIO   PR  NI    VIRT    RES    SHR S  %CPU %MEM     HORA+ ORDEN       
 1183 root      20   0  562648 118512  81972 R  59,8  3,0  33:08.72 Xorg        
 2032 gorremu   20   0 1667448 185472  47936 S  20,3  4,7  13:36.99 compiz      
 2552 gorremu   20   0  688088  41904  25456 S  14,3  1,1  13:08.40 gnome-syst+ 
 2238 gorremu   20   0  633056  52488  27112 S   6,6  1,3  20:23.47 my-weather+ 
 3044 gorremu   20   0 2405748 327212  80068 S   2,3  8,3   4:16.97 Web Content 
 7059 gorremu   20   0  668288  35768  28048 S   2,3  0,9   0:01.21 gnome-term+ 
 2620 gorremu   20   0 2844856 479388 171956 S   1,0 12,2  35:04.61 firefox     
 2674 gorremu   20   0 2515796 329748  81104 S   1,0  8,4   9:00.19 Web Content 
 4058 gorremu   20   0 8676228 357548 138452 S   1,0  9,1  30:42.00 Web Content 
    8 root      20   0       0      0      0 S   0,3  0,0   0:14.25 rcu_sched   
   16 root      20   0       0      0      0 S   0,3  0,0   0:05.49 ksoftirqd/1 
 1670 gorremu   20   0  528576  26008  19276 S   0,3  0,7   0:09.20 bamfdaemon  
 1894 gorremu   20   0  206864   6260   5628 S   0,3  0,2   0:03.28 at-spi2-re+ 
 2132 gorremu   20   0 3296064 187348  24448 S   0,3  4,8   1:30.16 dropbox     
 4822 gorremu   20   0 2553764 265340 116020 S   0,3  6,7   7:16.10 Web Content 
 5165 root      20   0       0      0      0 S   0,3  0,0   0:20.87 kworker/u1+ 
 5674 root      20   0       0      0      0 S   0,3  0,0   0:12.36 kworker/u1+ 

```

free -hm:

```
              total        used        free      shared  buff/cache   available
Memoria:        3,8G        2,2G        549M        363M        1,0G        942M
Swap:          3,9G         25M        3,9G

```

iostat:

```
Linux 4.13.0-36-generic (macross)     07/03/18     _x86_64_    (4 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
          17,77    0,09    3,59    0,91    0,00   77,63

Device:            tps    kB_read/s    kB_wrtn/s    kB_read    kB_wrtn
loop0             0,01         0,08         0,00       1102          0
loop1             0,99         1,06         0,00      15075          0
loop2             0,00         0,07         0,00       1056          0
loop3             0,01         0,08         0,00       1098          0
loop4             0,01         0,08         0,00       1119          0
sda               6,73       141,49       134,71    2011975    1915544

```

vmstat:

```
procs -----------memory---------- ---swap-- -----io---- -system-- ------cpu-----
 r  b   swpd  libre búfer caché   si   so    bi    bo   in   cs us sy id wa st
 6  0  26124 358056  53848 1177520    0    0    37    35  378  339 18  4 78  1  0

```

Hope this helps!

---

### Post by blade4 on 2018-03-07
From your **top **results it seems Xorg and compiz are using up a lot of CPU. This means there could be an issue with your graphics setup. 

Could you let us know what graphics card you're using ? Use the following command in the terminal: 
```
lspci -v |grep VGA
```

Also, could you let us know the output of the following code? 
```
[COLOR=#333333] glxinfo | grep render[/COLOR]
```

---

### Post by carega on 2018-03-07
Here are the outputs from the commands:

**lspci -v |grep VGA**:

```
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
```

**glxinfo | grep render**:

```
direct rendering: Yes
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
Extended renderer info (GLX_MESA_query_renderer):
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
    GL_ARB_conditional_render_inverted, GL_ARB_copy_buffer, GL_ARB_copy_image, 
    GL_MESA_texture_signed_rgba, GL_NV_conditional_render, GL_NV_depth_clamp, 
    GL_ARB_conditional_render_inverted, GL_ARB_copy_buffer, GL_ARB_copy_image, 
    GL_NV_conditional_render, GL_NV_depth_clamp, GL_NV_light_max_exponent, 
    GL_OES_element_index_uint, GL_OES_fbo_render_mipmap,
```

Thanks!

---

### Post by TheFu on 2018-03-08
So, looks like 80% of the CPU is busy doing GUI stuff. I normally see 10% or less of this on my 4G Chromebook.
Since you are using an Intel iGPU, the drivers for it should be already installed and maintained via APT.  Mine has 
xserver-xorg-video-intel-hwe-16.04          2:2.99.917+git20170309-0ubuntu1~16.04.1

You might be happier running a lighter desktop. XFCE, Mate, LXDE are all lighter especially when compared to the default Unity DE. 

I have an Intel iGPU and find Ubuntu-Mate to perform well. 
Don't have any ideas for making Unity work better. Sorry.

---

### Post by carega on 2018-03-08
The thing is that it doesn't happen all the time. But when it does it doesn't go back to smooth sailing like it before unless I restart the computer. Yes, I might consider a lighter desktop but I fear the same thing might happen anyway.

---

### Post by TheFu on 2018-03-08
> **carega said:**
> The thing is that it doesn't happen all the time. But when it does it doesn't go back to smooth sailing like it before unless I restart the computer. Yes, I might consider a lighter desktop but I fear the same thing might happen anyway.

Compiz is a compositing addon for powerful desktops.  It isn't needed for a nice, responsive desktop.  X11 paired with compiz can get stuck trying to do fancy graphics - like Unity is requesting.  Other desktops won't do that.

You don't have to de-install anything.  Just add a different desktop, pick it just before login, try it out and see that compiz isn't used and X11 doesn't eat as much CPU.  The risks are minimal if you make a fresh new userid for the testing.  Adding a different DE is about 3min of effort.  It definitely is NOT a new Ubuntu install.
 
If you don't like the new DE - uninstall it and delete the test userid.

---

### Post by carega on 2018-03-08
Fair enough, I'lll give it a try. How do I install a different desktop and which one would you recommend to try first out of the ones you mentioned?

---

### Post by monkeybrain20122 on 2018-03-08
Your specs is more than adequate to run compiz and then some. You said your computer "suddenly become slow", that means it wasn't slow before and therefore it cannot be because your machine is not powerful enough, otherwise it would have been always slow. It is a myth from around 7 years ago that you need a super powerful machine to run unity apparently from people either have a preference for "light desktops" or using very old hardware which is either very low in specs or does not support composting (more likely both). Any machine that can run a modern Windows OS would be more than enough for Unity (except maybe netbooks) 

If this happens after you "upgrade" then my guess is that the upgrade is the problem. Probably some old settings interfere with the new OS.  That happened to me on one machine, I didn't "upgrade" but I kept the /home partition (hence all old settings) and after reinstall Uninty behaved exactly as you described. Wiping out the /home and reinstalling fixed it. You can try bandaid solutions like installing a "light" desktop but if I were you I would do a clean installl.

---

### Post by carega on 2018-03-08
> if I were you I would do a clean installl.

I had originally upgraded from 14.04 and started experiencing these problems. People gave me your exact recommendation which I tried but it didn't really solve anything. I've noticed it starts lagging when I open facebook + youtube + some other website. The thing is after I close these or even browser it continues running slow unless I reboot. On rare occasions if I disable Wifi, close some processes and just have a lot of patience it goes back to normal.

---

### Post by monkeybrain20122 on 2018-03-08
> **carega said:**
> I had originally upgraded from 14.04 and started experiencing these problems. People gave me your exact recommendation which I tried but it didn't really solve anything. I've noticed it starts lagging when I open facebook + youtube + some other website. The thing is after I close these or even browser it continues running slow unless I reboot. On rare occasions if I disable Wifi, close some processes and just have a lot of patience it goes back to normal.
 Does it happen with all browsers or just Firefox?

---

### Post by monkeybrain20122 on 2018-03-08
Could be a graphic driver problem.

so pleas do 
```
sudo apt install mesa-utils
```
after mesa-utils is installed

```
glxinfo | grep OpenGL

glxinfo | grep rendering
```

---

### Post by carega on 2018-03-08
> **monkeybrain20122 said:**
> Does it happen with all browsers or just Firefox?

Since I did the clean install I haven't tried another browser. Should I try with Opera or some light browser you can recommend?

glxinfo | grep OpenGL:

```
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
OpenGL core profile version string: 3.3 (Core Profile) Mesa 18.1.0-devel
OpenGL core profile shading language version string: 3.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 18.1.0-devel
OpenGL shading language version string: 1.40
OpenGL context flags: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.0 Mesa 18.1.0-devel
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.00
OpenGL ES profile extensions:

```

glxinfo | grep rendering

```
direct rendering: Yes

```

---

### Post by monkeybrain20122 on 2018-03-08
Which Ubuntu is this? Why do you have mesa 18.1.0 dev? The latest stable release is 17.3.2

You can try chromium from the repository since this is just a test.

Also in Firefox go to the url bar and type about:support then scroll down to graphic and post the section.

---

### Post by carega on 2018-03-08
I'm going to try Chromium for the next few days and see what happens.

I don't know why I have mesa 18.1.0 dev... I don't even know what that is, sorry. I have Ubuntu 16.04

Regarding Firefox:

```
Gráficos
Características
Compositing    Basic
Asynchronous Pan/Zoom    rueda habilitada; arrastre de barra de desplazamiento habilitado; teclado habilitado; desplazamiento automático habilitado
Información WSI del controlador WebGL 1    GLX 1.4
GLX_VENDOR(client): Mesa Project and SGI
GLX_VENDOR(server): SGI
Extensions: GLX_ARB_create_context GLX_ARB_create_context_profile GLX_ARB_create_context_robustness GLX_ARB_fbconfig_float GLX_ARB_framebuffer_sRGB GLX_ARB_get_proc_address GLX_ARB_multisample GLX_EXT_buffer_age GLX_EXT_create_context_es2_profile GLX_EXT_create_context_es_profile GLX_EXT_fbconfig_packed_float GLX_EXT_framebuffer_sRGB GLX_EXT_import_context GLX_EXT_texture_from_pixmap GLX_EXT_visual_info GLX_EXT_visual_rating GLX_INTEL_swap_event GLX_MESA_copy_sub_buffer GLX_MESA_multithread_makecurrent GLX_MESA_query_renderer GLX_MESA_swap_control GLX_OML_swap_method GLX_OML_sync_control GLX_SGIS_multisample GLX_SGIX_fbconfig GLX_SGIX_pbuffer GLX_SGIX_visual_select_group GLX_SGI_make_current_read GLX_SGI_swap_control GLX_SGI_video_sync 
Procesador WebGL 1    Intel Open Source Technology Center -- Mesa DRI Intel(R) Sandybridge Mobile 
Versión del controlador WebGL 1    3.0 Mesa 18.1.0-devel
Extensiones del controlador WebGL 1    GL_3DFX_texture_compression_FXT1 GL_AMD_draw_buffers_blend GL_AMD_seamless_cubemap_per_texture GL_AMD_shader_trinary_minmax GL_ANGLE_texture_compression_dxt3 GL_ANGLE_texture_compression_dxt5 GL_APPLE_object_purgeable GL_APPLE_packed_pixels GL_ARB_ES2_compatibility GL_ARB_ES3_compatibility GL_ARB_arrays_of_arrays GL_ARB_blend_func_extended GL_ARB_buffer_storage GL_ARB_clear_buffer_object GL_ARB_clear_texture GL_ARB_clip_control GL_ARB_color_buffer_float GL_ARB_compressed_texture_pixel_storage GL_ARB_conditional_render_inverted GL_ARB_copy_buffer GL_ARB_copy_image GL_ARB_cull_distance GL_ARB_debug_output GL_ARB_depth_buffer_float GL_ARB_depth_clamp GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_draw_buffers_blend GL_ARB_draw_elements_base_vertex GL_ARB_draw_instanced GL_ARB_explicit_attrib_location GL_ARB_explicit_uniform_location GL_ARB_fragment_coord_conventions GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_framebuffer_object GL_ARB_framebuffer_sRGB GL_ARB_get_program_binary GL_ARB_get_texture_sub_image GL_ARB_half_float_pixel GL_ARB_half_float_vertex GL_ARB_instanced_arrays GL_ARB_internalformat_query GL_ARB_internalformat_query2 GL_ARB_invalidate_subdata GL_ARB_map_buffer_alignment GL_ARB_map_buffer_range GL_ARB_multi_bind GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_occlusion_query2 GL_ARB_pipeline_statistics_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_polygon_offset_clamp GL_ARB_program_interface_query GL_ARB_provoking_vertex GL_ARB_robustness GL_ARB_sample_shading GL_ARB_sampler_objects GL_ARB_seamless_cube_map GL_ARB_seamless_cubemap_per_texture GL_ARB_separate_shader_objects GL_ARB_shader_bit_encoding GL_ARB_shader_draw_parameters GL_ARB_shader_group_vote GL_ARB_shader_objects GL_ARB_shader_texture_lod GL_ARB_shading_language_100 GL_ARB_shading_language_420pack GL_ARB_shading_language_packing GL_ARB_shadow GL_ARB_sync GL_ARB_texture_barrier GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_compression_rgtc GL_ARB_texture_cube_map GL_ARB_texture_cube_map_array GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_filter_anisotropic GL_ARB_texture_float GL_ARB_texture_gather GL_ARB_texture_mirror_clamp_to_edge GL_ARB_texture_mirrored_repeat GL_ARB_texture_multisample GL_ARB_texture_non_power_of_two GL_ARB_texture_query_levels GL_ARB_texture_query_lod GL_ARB_texture_rectangle GL_ARB_texture_rg GL_ARB_texture_rgb10_a2ui GL_ARB_texture_storage GL_ARB_texture_storage_multisample GL_ARB_texture_swizzle GL_ARB_timer_query GL_ARB_transform_feedback2 GL_ARB_transform_feedback_overflow_query GL_ARB_transpose_matrix GL_ARB_uniform_buffer_object GL_ARB_vertex_array_bgra GL_ARB_vertex_array_object GL_ARB_vertex_attrib_binding GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_vertex_type_10f_11f_11f_rev GL_ARB_vertex_type_2_10_10_10_rev GL_ARB_window_pos GL_ATI_blend_equation_separate GL_ATI_draw_buffers GL_ATI_separate_stencil GL_ATI_texture_env_combine3 GL_ATI_texture_float GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_copy_texture GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_multisample_blit_scaled GL_EXT_framebuffer_object GL_EXT_framebuffer_sRGB GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_float GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_polygon_offset_clamp GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shader_framebuffer_fetch_non_coherent GL_EXT_shader_integer_mix GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_array GL_EXT_texture_compression_dxt1 GL_EXT_texture_compression_rgtc GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_integer GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_texture_sRGB_decode GL_EXT_texture_shared_exponent GL_EXT_texture_snorm GL_EXT_texture_swizzle GL_EXT_timer_query GL_EXT_transform_feedback GL_EXT_vertex_array GL_EXT_vertex_array_bgra GL_IBM_multimode_draw_arrays GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_INTEL_performance_query GL_KHR_blend_equation_advanced GL_KHR_context_flush_control GL_KHR_debug GL_KHR_no_error GL_KHR_robustness GL_MESA_pack_invert GL_MESA_shader_integer_functions GL_MESA_texture_signed_rgba GL_MESA_window_pos GL_NV_blend_square GL_NV_conditional_render GL_NV_depth_clamp GL_NV_light_max_exponent GL_NV_packed_depth_stencil GL_NV_primitive_restart GL_NV_texgen_reflection GL_NV_texture_barrier GL_NV_texture_env_combine4 GL_NV_texture_rectangle GL_OES_EGL_image GL_OES_read_format GL_S3_s3tc GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays 
Extensiones WebGL 1    ANGLE_instanced_arrays EXT_blend_minmax EXT_color_buffer_half_float EXT_frag_depth EXT_sRGB EXT_shader_texture_lod EXT_texture_filter_anisotropic EXT_disjoint_timer_query OES_element_index_uint OES_standard_derivatives OES_texture_float OES_texture_float_linear OES_texture_half_float OES_texture_half_float_linear OES_vertex_array_object WEBGL_color_buffer_float WEBGL_compressed_texture_etc WEBGL_compressed_texture_s3tc WEBGL_compressed_texture_s3tc_srgb WEBGL_debug_renderer_info WEBGL_debug_shaders WEBGL_depth_texture WEBGL_draw_buffers WEBGL_lose_context
Información WSI del controlador WebGL 2    GLX 1.4
GLX_VENDOR(client): Mesa Project and SGI
GLX_VENDOR(server): SGI
Extensions: GLX_ARB_create_context GLX_ARB_create_context_profile GLX_ARB_create_context_robustness GLX_ARB_fbconfig_float GLX_ARB_framebuffer_sRGB GLX_ARB_get_proc_address GLX_ARB_multisample GLX_EXT_buffer_age GLX_EXT_create_context_es2_profile GLX_EXT_create_context_es_profile GLX_EXT_fbconfig_packed_float GLX_EXT_framebuffer_sRGB GLX_EXT_import_context GLX_EXT_texture_from_pixmap GLX_EXT_visual_info GLX_EXT_visual_rating GLX_INTEL_swap_event GLX_MESA_copy_sub_buffer GLX_MESA_multithread_makecurrent GLX_MESA_query_renderer GLX_MESA_swap_control GLX_OML_swap_method GLX_OML_sync_control GLX_SGIS_multisample GLX_SGIX_fbconfig GLX_SGIX_pbuffer GLX_SGIX_visual_select_group GLX_SGI_make_current_read GLX_SGI_swap_control GLX_SGI_video_sync 
Procesador WebGL2    Intel Open Source Technology Center -- Mesa DRI Intel(R) Sandybridge Mobile 
Versión del controlador WebGL 2    3.3 (Core Profile) Mesa 18.1.0-devel
Extensiones del controlador WebGL 2    GL_3DFX_texture_compression_FXT1 GL_AMD_draw_buffers_blend GL_AMD_seamless_cubemap_per_texture GL_AMD_shader_trinary_minmax GL_AMD_vertex_shader_layer GL_AMD_vertex_shader_viewport_index GL_ANGLE_texture_compression_dxt3 GL_ANGLE_texture_compression_dxt5 GL_APPLE_object_purgeable GL_ARB_ES2_compatibility GL_ARB_ES3_compatibility GL_ARB_arrays_of_arrays GL_ARB_base_instance GL_ARB_blend_func_extended GL_ARB_buffer_storage GL_ARB_clear_buffer_object GL_ARB_clear_texture GL_ARB_clip_control GL_ARB_compressed_texture_pixel_storage GL_ARB_conditional_render_inverted GL_ARB_copy_buffer GL_ARB_copy_image GL_ARB_cull_distance GL_ARB_debug_output GL_ARB_depth_buffer_float GL_ARB_depth_clamp GL_ARB_direct_state_access GL_ARB_draw_buffers GL_ARB_draw_buffers_blend GL_ARB_draw_elements_base_vertex GL_ARB_draw_instanced GL_ARB_enhanced_layouts GL_ARB_explicit_attrib_location GL_ARB_explicit_uniform_location GL_ARB_fragment_coord_conventions GL_ARB_fragment_layer_viewport GL_ARB_fragment_shader GL_ARB_framebuffer_object GL_ARB_framebuffer_sRGB GL_ARB_get_program_binary GL_ARB_get_texture_sub_image GL_ARB_half_float_pixel GL_ARB_half_float_vertex GL_ARB_instanced_arrays GL_ARB_internalformat_query GL_ARB_internalformat_query2 GL_ARB_invalidate_subdata GL_ARB_map_buffer_alignment GL_ARB_map_buffer_range GL_ARB_multi_bind GL_ARB_occlusion_query2 GL_ARB_pipeline_statistics_query GL_ARB_pixel_buffer_object GL_ARB_point_sprite GL_ARB_polygon_offset_clamp GL_ARB_program_interface_query GL_ARB_provoking_vertex GL_ARB_robustness GL_ARB_sample_shading GL_ARB_sampler_objects GL_ARB_seamless_cube_map GL_ARB_seamless_cubemap_per_texture GL_ARB_separate_shader_objects GL_ARB_shader_bit_encoding GL_ARB_shader_draw_parameters GL_ARB_shader_group_vote GL_ARB_shader_objects GL_ARB_shader_subroutine GL_ARB_shader_texture_lod GL_ARB_shader_viewport_layer_array GL_ARB_shading_language_420pack GL_ARB_shading_language_packing GL_ARB_sync GL_ARB_texture_barrier GL_ARB_texture_buffer_object GL_ARB_texture_buffer_object_rgb32 GL_ARB_texture_buffer_range GL_ARB_texture_compression_rgtc GL_ARB_texture_cube_map_array GL_ARB_texture_filter_anisotropic GL_ARB_texture_float GL_ARB_texture_gather GL_ARB_texture_mirror_clamp_to_edge GL_ARB_texture_multisample GL_ARB_texture_non_power_of_two GL_ARB_texture_query_levels GL_ARB_texture_query_lod GL_ARB_texture_rectangle GL_ARB_texture_rg GL_ARB_texture_rgb10_a2ui GL_ARB_texture_storage GL_ARB_texture_storage_multisample GL_ARB_texture_swizzle GL_ARB_timer_query GL_ARB_transform_feedback2 GL_ARB_transform_feedback_overflow_query GL_ARB_uniform_buffer_object GL_ARB_vertex_array_bgra GL_ARB_vertex_array_object GL_ARB_vertex_attrib_binding GL_ARB_vertex_shader GL_ARB_vertex_type_10f_11f_11f_rev GL_ARB_vertex_type_2_10_10_10_rev GL_ARB_viewport_array GL_ATI_blend_equation_separate GL_ATI_texture_float GL_EXT_abgr GL_EXT_blend_equation_separate GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_multisample_blit_scaled GL_EXT_framebuffer_sRGB GL_EXT_packed_depth_stencil GL_EXT_packed_float GL_EXT_pixel_buffer_object GL_EXT_polygon_offset_clamp GL_EXT_provoking_vertex GL_EXT_shader_framebuffer_fetch_non_coherent GL_EXT_shader_integer_mix GL_EXT_texture_array GL_EXT_texture_compression_dxt1 GL_EXT_texture_compression_rgtc GL_EXT_texture_compression_s3tc GL_EXT_texture_filter_anisotropic GL_EXT_texture_integer GL_EXT_texture_sRGB GL_EXT_texture_sRGB_decode GL_EXT_texture_shared_exponent GL_EXT_texture_snorm GL_EXT_texture_swizzle GL_EXT_timer_query GL_EXT_transform_feedback GL_EXT_vertex_array_bgra GL_IBM_multimode_draw_arrays GL_INTEL_performance_query GL_KHR_blend_equation_advanced GL_KHR_context_flush_control GL_KHR_debug GL_KHR_no_error GL_KHR_robustness GL_MESA_pack_invert GL_MESA_shader_integer_functions GL_MESA_texture_signed_rgba GL_NV_conditional_render GL_NV_depth_clamp GL_NV_packed_depth_stencil GL_NV_texture_barrier GL_OES_EGL_image GL_S3_s3tc
Extensiones WebGL 2    EXT_color_buffer_float EXT_texture_filter_anisotropic EXT_disjoint_timer_query OES_texture_float_linear WEBGL_compressed_texture_etc WEBGL_compressed_texture_s3tc WEBGL_compressed_texture_s3tc_srgb WEBGL_debug_renderer_info WEBGL_debug_shaders WEBGL_lose_context
GPU #1
Activa    Si
Descripción    Intel Open Source Technology Center -- Mesa DRI Intel(R) Sandybridge Mobile 
ID de vendedor    Intel Open Source Technology Center
ID de dispositivo    Mesa DRI Intel(R) Sandybridge Mobile 
Versión de driver    3.0 Mesa 18.1.0-devel
Diagnósticos
AzureCanvasAccelerated    0
AzureCanvasBackend    skia
AzureContentBackend    skia
AzureFallbackCanvasBackend    none
CairoUseXRender    0
Registro de decisión
HW_COMPOSITING    
blocked by default: Acceleration blocked by platform
OPENGL_COMPOSITING    
unavailable by default: Hardware compositing is disabled
WEBRENDER    
opt-in by default: WebRender is an opt-in feature
unavailable by runtime: Build doesn't include WebRender
OMTP    
disabled by default: Disabled by default
```

---

### Post by monkeybrain20122 on 2018-03-08
Well before you try anything else I think maybe your graphic driver (basically from mesa) is the problem. Did you install mesa from a ppa or download something from intel? I would downgrade mesa first.

First have to find out where your mesa comes from 

do the following and post the outputs please
```
grep ^ /etc/apt/sources.list /etc/apt/sources.list.d/*
```

---

### Post by carega on 2018-03-08
I believe I downloaded something from Intel AND install mesa from a ppa  that always tells me to install them again, for some reason.

The results:
```
/etc/apt/sources.list:# deb cdrom:[Ubuntu 16.04.3 LTS _Xenial Xerus_ - Release amd64 (20170801)]/ xenial main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
/etc/apt/sources.list:# newer versions of the distribution.
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu xenial main restricted
/etc/apt/sources.list:# deb-src http://ar.archive.ubuntu.com/ubuntu/ xenial main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:## Major bug fix updates produced after the final release of the
/etc/apt/sources.list:## distribution.
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu xenial-updates main restricted
/etc/apt/sources.list:# deb-src http://ar.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
/etc/apt/sources.list:## team. Also, please note that software in universe WILL NOT receive any
/etc/apt/sources.list:## review or updates from the Ubuntu security team.
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu xenial universe
/etc/apt/sources.list:# deb-src http://ar.archive.ubuntu.com/ubuntu/ xenial universe
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu xenial-updates universe
/etc/apt/sources.list:# deb-src http://ar.archive.ubuntu.com/ubuntu/ xenial-updates universe
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
/etc/apt/sources.list:## team, and may not be under a free licence. Please satisfy yourself as to 
/etc/apt/sources.list:## your rights to use the software. Also, please note that software in 
/etc/apt/sources.list:## multiverse WILL NOT receive any review or updates from the Ubuntu
/etc/apt/sources.list:## security team.
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu xenial multiverse
/etc/apt/sources.list:# deb-src http://ar.archive.ubuntu.com/ubuntu/ xenial multiverse
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu xenial-updates multiverse
/etc/apt/sources.list:# deb-src http://ar.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository may not have been tested as
/etc/apt/sources.list:## extensively as that contained in the main release, although it includes
/etc/apt/sources.list:## newer versions of some applications which may provide useful features.
/etc/apt/sources.list:## Also, please note that software in backports WILL NOT receive any review
/etc/apt/sources.list:## or updates from the Ubuntu security team.
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu xenial-backports main restricted universe multiverse
/etc/apt/sources.list:# deb-src http://ar.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:## Uncomment the following two lines to add software from Canonical's
/etc/apt/sources.list:## 'partner' repository.
/etc/apt/sources.list:# This software is not part of Ubuntu, but is offered by Canonical and the
/etc/apt/sources.list:# respective vendors as a service to Ubuntu users.
/etc/apt/sources.list:deb http://archive.canonical.com/ubuntu xenial partner
/etc/apt/sources.list:deb-src http://archive.canonical.com/ubuntu xenial partner
/etc/apt/sources.list:
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu xenial-security main restricted
/etc/apt/sources.list:# deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu xenial-security universe
/etc/apt/sources.list:# deb-src http://security.ubuntu.com/ubuntu xenial-security universe
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu xenial-security multiverse
/etc/apt/sources.list:# deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse
/etc/apt/sources.list:deb https://dl.winehq.org/wine-builds/ubuntu/ xenial main
/etc/apt/sources.list:# deb-src https://dl.winehq.org/wine-builds/ubuntu/ xenial main
/etc/apt/sources.list:# deb-src https://dl.winehq.org/wine-builds/ubuntu/ xenial main
/etc/apt/sources.list:deb http://download.virtualbox.org/virtualbox/debian xenial contrib
/etc/apt/sources.list:# deb-src http://download.virtualbox.org/virtualbox/debian xenial contrib
/etc/apt/sources.list.d/atareao-ubuntu-atareao-xenial.list:deb http://ppa.launchpad.net/atareao/atareao/ubuntu xenial main
/etc/apt/sources.list.d/atareao-ubuntu-atareao-xenial.list:# deb-src http://ppa.launchpad.net/atareao/atareao/ubuntu xenial main
/etc/apt/sources.list.d/atareao-ubuntu-atareao-xenial.list.save:deb http://ppa.launchpad.net/atareao/atareao/ubuntu xenial main
/etc/apt/sources.list.d/atareao-ubuntu-atareao-xenial.list.save:# deb-src http://ppa.launchpad.net/atareao/atareao/ubuntu xenial main
/etc/apt/sources.list.d/getdeb.list:deb http://archive.getdeb.net/ubuntu xenial-getdeb games
/etc/apt/sources.list.d/getdeb.list.save:deb http://archive.getdeb.net/ubuntu xenial-getdeb games
/etc/apt/sources.list.d/intellinuxgraphics.list:deb https://download.01.org/gfx/ubuntu/16.04/main xenial main #Intel Graphics drivers
/etc/apt/sources.list.d/intellinuxgraphics.list.save:deb https://download.01.org/gfx/ubuntu/16.04/main xenial main #Intel Graphics drivers
/etc/apt/sources.list.d/megasync.list:deb https://mega.nz/linux/MEGAsync/xUbuntu_16.04/ ./
/etc/apt/sources.list.d/megasync.list.save:deb https://mega.nz/linux/MEGAsync/xUbuntu_16.04/ ./
/etc/apt/sources.list.d/nilarimogard-ubuntu-webupd8-xenial.list:deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu xenial main
/etc/apt/sources.list.d/nilarimogard-ubuntu-webupd8-xenial.list:# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu xenial main
/etc/apt/sources.list.d/nilarimogard-ubuntu-webupd8-xenial.list.save:deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu xenial main
/etc/apt/sources.list.d/nilarimogard-ubuntu-webupd8-xenial.list.save:# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu xenial main
/etc/apt/sources.list.d/oibaf-ubuntu-graphics-drivers-xenial.list:deb http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu xenial main
/etc/apt/sources.list.d/oibaf-ubuntu-graphics-drivers-xenial.list:# deb-src http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu xenial main
/etc/apt/sources.list.d/oibaf-ubuntu-graphics-drivers-xenial.list:# deb-src http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu xenial main
/etc/apt/sources.list.d/oibaf-ubuntu-graphics-drivers-xenial.list.save:deb http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu xenial main
/etc/apt/sources.list.d/oibaf-ubuntu-graphics-drivers-xenial.list.save:# deb-src http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu xenial main
/etc/apt/sources.list.d/oibaf-ubuntu-graphics-drivers-xenial.list.save:# deb-src http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu xenial main
/etc/apt/sources.list.d/otto-kesselgulasch-ubuntu-gimp-xenial.list:deb http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu xenial main
/etc/apt/sources.list.d/otto-kesselgulasch-ubuntu-gimp-xenial.list:# deb-src http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu xenial main
/etc/apt/sources.list.d/otto-kesselgulasch-ubuntu-gimp-xenial.list.save:deb http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu xenial main
/etc/apt/sources.list.d/otto-kesselgulasch-ubuntu-gimp-xenial.list.save:# deb-src http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu xenial main
/etc/apt/sources.list.d/playdeb.list:deb http://archive.getdeb.net/ubuntu xenial-getdeb games
/etc/apt/sources.list.d/playdeb.list.save:deb http://archive.getdeb.net/ubuntu xenial-getdeb games
/etc/apt/sources.list.d/skype-stable.list:deb [arch=amd64] https://repo.skype.com/deb stable main
/etc/apt/sources.list.d/skype-stable.list.save:deb [arch=amd64] https://repo.skype.com/deb stable main
/etc/apt/sources.list.d/thebernmeister-ubuntu-ppa-xenial.list:deb http://ppa.launchpad.net/thebernmeister/ppa/ubuntu xenial main
/etc/apt/sources.list.d/thebernmeister-ubuntu-ppa-xenial.list:# deb-src http://ppa.launchpad.net/thebernmeister/ppa/ubuntu xenial main
/etc/apt/sources.list.d/thebernmeister-ubuntu-ppa-xenial.list.save:deb http://ppa.launchpad.net/thebernmeister/ppa/ubuntu xenial main
/etc/apt/sources.list.d/thebernmeister-ubuntu-ppa-xenial.list.save:# deb-src http://ppa.launchpad.net/thebernmeister/ppa/ubuntu xenial main

```

---

### Post by carega on 2018-03-08
Sorry, just realized the last sentece I wrote was not too coherent.

I downloaded some Intel program that does upgrades. Also I believe I added a PPA that updates graphics drivers (oibaf I believe). I did these things in an effort to stop the lagging problem.

Also, I think ever since I added the PPA (I think) I get messages to download and install some packages (the same packages every time!) that have "mesa" in them. It happens every few days, for some reason they get deleted or maybe the get updated fairly quickly?

the packages in question:

```
Se actualizarán los siguientes paquetes:
  friendly-recovery libdrm-amdgpu1 libdrm-amdgpu1:i386 libdrm-common
  libdrm-intel1 libdrm-intel1:i386 libdrm-nouveau2 libdrm-nouveau2:i386
  libdrm-radeon1 libdrm-radeon1:i386 libdrm2 libdrm2:i386 libegl1-mesa
  libegl1-mesa-drivers libgbm1 libgl1-mesa-dri libgl1-mesa-dri:i386
  libgl1-mesa-glx libgl1-mesa-glx:i386 libglapi-mesa libglapi-mesa:i386
  libgles1-mesa libgles2-mesa libllvm6.0 libllvm6.0:i386 libosmesa6
  libosmesa6:i386 libwayland-egl1-mesa libxatracker2 mesa-vdpau-drivers
30 actualizados, 0 nuevos se instalarán, 0 para eliminar y 0 no actualizados.
```

---

### Post by monkeybrain20122 on 2018-03-08
Yes oibaf upgrades very quickly because it is experimental. IIRC it upgrades twice a day.

Now I think first of all we should downgrade the mesa packages from oibaf 

First install ppa-purge if not already installed
```

sudo apt install ppa-purge
```

Now to do a ppa-purge on oibaf make sure that the ppa is enabled. Easy way, go to the dash type software. It will bring up the software and updates gui, go to other software and make sure that the box for oibaf is checked, then close Software & updates.

Now purge oibaf and downgrade all the packages installed from there
```

sudo ppa-purge ppa:oibaf/graphics-drivers
```

and follow the prompt.
Then reboot
Now mesa will be downgraded to the next highest version, namely those from the intel repository, maybe we'll have to purge that too if this doesn't work, but we'll see.

---

### Post by TheFu on 2018-03-08
Yes, remove the 01.org PPA from intel.  It has been gone for some months.  At least I got a 403 on it for weeks before removing it - maybe in January.

---

### Post by TheFu on 2018-03-08
That extra info is helpful.   I **am** a lite-desktop person. I can admit it.  ;) On a 4G system with 2 cores, I'd rather have RAM used for programs than a pretty interface.  

I had a similar issue on my chromebook running 16.04 with firefox about a year ago and tried to solve it using intel GPU drivers, at least initially.  It didn't help and it tried loading the drivers from 01.org where the PPA was.  That PPA stopped working (403) and I removed it.

The solution I used was multi-faceted. 
* HWE kernel updates  [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)
* Increase swap to 4.1G - with browsers eating 3+G, 
* Change swap to be compressed [https://ubuntu-mate.community/t/enable-zswap-to-increase-performance/11302](https://ubuntu-mate.community/t/enable-zswap-to-increase-performance/11302)
* stay with the stock, included, intel GPU drivers
Doing this was effective. It stopped the slowdowns and I could have 15 tabs open in firefox - provided I limited the number a FF addons to about 5 or less.  I do not have flash installed for FF.

But last week that system had an SSD failure and I reloaded a fresh 16.04.4 Mate onto a different SSD, then restored my settings, programs and data. It has behaved well so far. 

zswap is counter intuitive.  It may be on by default. ```
 dmesg | grep -i zswap
``` will show if it is enabled. It is on mine, but that could be due to my selective restore for /etc/ files.

To load ubuntu-mate, just install that package.  This should be a metapackage that includes the DE, but not all the other mate-specific programs.  For those, ubuntu-mate-desktop is the package.  Don't forget to create a new userid for testing. If you don't, some settings in ~/.config/ may conflict between different DEs.  Best to avoid any issues while troubleshooting.

For most end-users, the easiest way to make a backup of the things they care about is aptik. I've never used it, but it claims to get your HOME and themes and lists of installed packages.  Those basic things should make a reinstall fairly painless for a normal desktop user. That's the theory.

---

### Post by carega on 2018-03-09
Well I purged oibaf and so far it's working ok, I run epsxe and it lags but instead of remaining slow the computer goes back to normal once I close the program. However I still find it strange that it lags considering that when I used this computer to play while using ubuntu 12.04 it ran smoothly.

---

### Post by monkeybrain20122 on 2018-03-09
> **carega said:**
> However I still find it strange that it lags considering that when I used this computer to play while using ubuntu 12.04 it ran smoothly.

Can you post the outputs again for 
```
glxinfo | grep OpenGL
```

---

### Post by carega on 2018-03-09
Sure:

```
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
OpenGL core profile version string: 3.3 (Core Profile) Mesa 17.2.8
OpenGL core profile shading language version string: 3.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 17.2.8
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.0 Mesa 17.2.8
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.00
OpenGL ES profile extensions:

```

Thank you for helping me!

---

### Post by kerry_s on 2018-03-10
you can use unity tweak, to disable effects, animation, blur, etc... to lighten the load on the gpu, it will feel much faster.
using ubuntu 17 is a much better option.

i'm using ubuntu 18, i got the same vid as you.
[ATTACH=CONFIG]278884[/ATTACH]

---

### Post by monkeybrain20122 on 2018-03-10
That seems ok, but just update mesa to 17.3.6 and see if this improve the game. [https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/pkppa](https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/pkppa)

I don't know about epsxe and it seems to be a paid game so I can't test it. But maybe there are some settings you can fiddle with? Do they have a help forum?

Edited :In the terminal type 

glxgears

Does the motion look smooth?

---

### Post by monkeybrain20122 on 2018-03-10
> **kerry_s said:**
> you can use unity tweak, to disable effects, animation, blur, etc... to lighten the load on the gpu, it will feel much faster.
using ubuntu 17 is a much better option.



I beg to differ. I find Ubuntu 17.10 kind of buggy (I tested it on my spare drive and there are numerous threads by others here) and it will expire in a few months. It also defaults to gnome shell which is very laggy (though Unity can be installed), many things don't work in  wayland (yes, it is easy to switch to x, but still ..)

Also I don't think OP has any issue with gpu being "slow" after purging oibaf ppa, only one game is slow, IMO it is drastic to cripple your OS just for one game, yes, IMO to disable all animations etc in a modern DE is crippling the OS, if op prefers a bland win98-ish interface he could always go Lubuntu. :)

---

### Post by carega on 2018-03-10
> **monkeybrain20122 said:**
> That seems ok, but just update mesa to 17.3.6 and see if this improve the game. [https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/pkppa](https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/pkppa)

I don't know about epsxe and it seems to be a paid game so I can't test it. But maybe there are some settings you can fiddle with? Do they have a help forum?

Edited :In the terminal type 

glxgears

Does the motion look smooth?

Yes, the motion looks pretty smooth. Here's the output from the terminal:


```
gorremu@macross:~$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
342 frames in 5.0 seconds = 68.341 FPS
299 frames in 5.0 seconds = 59.617 FPS
299 frames in 5.0 seconds = 59.616 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
      after 1121 requests (310 known processed) with 0 events remaining.
```

It's not epsxe, it's actually PCSX (though I guess it doesn't make much difference. The same happens when I play Mupen64plus-Qt. It starts ok but it eventually starts lagging, both video and sound. It didn't happen with ubuntu 12.04 (man I miss playing Ocarina of Time!).

Here's the output once I updated the mesa drive:

```
gorremu@macross:~$ glxgears
351 frames in 5.0 seconds = 70.077 FPS
299 frames in 5.0 seconds = 59.727 FPS
299 frames in 5.0 seconds = 59.719 FPS
299 frames in 5.0 seconds = 59.712 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
      after 1574 requests (321 known processed) with 0 events remaining.
```

---

### Post by monkeybrain20122 on 2018-03-10
so your system works normally and glxgears performance is good, driver is up to date. Basically everything is in good order except for those games

I don't know anything about those console emulators, but google turned up [https://forums.libretro.com/t/mupen64plus-is-unplayable-slow-on-linux-runs-full-speed-on-windows/10058/8](https://forums.libretro.com/t/mupen64plus-is-unplayable-slow-on-linux-runs-full-speed-on-windows/10058/8)

So maybe you just go to [git hub]("https://github.com/dh4/mupen64plus-qt/releases") and download the latest version and see if it works better, there is no need to compile.

---

### Post by carega on 2018-03-10
Thanks, I'm gonna check out those links!

---

### Post by TheFu on 2018-03-10
> **carega said:**
> Thanks, I'm gonna check out those links!

And switching to a lighter DE might still help.

---

### Post by monkeybrain20122 on 2018-03-10
> **TheFu said:**
> And switching to a lighter DE might still help.

No one with specs like OP's should be compelled to run a "light DE". I have a computer with similar specs and it is fast including games. Maybe some of those console emulators don't play well with composting but it has nothing to do with "light". With reasonably modern hardware the resource used on running any Linux DE is negligible, "light DE" is just a personal preference, it makes no difference performance wise in most cases (I cannot tell the difference in performance whether with Unity of xfce for my machine which is 6 years old)

---

### Post by TheFu on 2018-03-10
> **monkeybrain20122 said:**
> No one with specs like OP's should be compelled to run a "light DE". I have a computer with similar specs and it is fast including games. Maybe some of those console emulators don't play well with composting but it has nothing to do with "light". With reasonably modern hardware the resource used on running any Linux DE is negligible, "light DE" is just a personal preference, it makes no difference performance wise in most cases (I cannot tell the difference in performance whether with Unity of xfce for my machine which is 6 years old)

Exactly, what is the risk to the OP for trying?

Unity/Gnome3 or even Mate DO feel slower than openbox/fvwm on my core i3-5015u w/ 4G of RAM.

But everyone has to decide which trade-offs they are willing to accept.

---

### Post by monkeybrain20122 on 2018-03-10
> **TheFu said:**
> Exactly, what is the risk to the OP for trying?

Unity/Gnome3 or even Mate DO feel slower than openbox/fvwm on my core i3-5015u w/ 4G of RAM.

But everyone has to decide which trade-offs they are willing to accept.

What is the catch? Installing a whole bunch of junks you don't need. Running two DE's is a mess, tried it and certainly doesn't sit well with your minimalist approach :)

Yeah I am sure it will be real fast if you get rid of the DE altogether. Even my modest laptop has enough ram and cpu power to run a modern OS without noticeable lag in performance (4 Gs of ram, core i5), and I have to work with my computer a lot, so I would like it to be pleasant, FVWM, thanks but no thanks, I would rather spare a bit more resources than to have to work with something that looks like Windows from last century all day. :) (gnome shell does feel slow and jerky, but I think that has something to do with its way of handling graphics and animations than its 'weight', but it is clunky in design in general and doesn't make for very good work flow IMO, I also find KDE complicated to navigate but it has nothing to do with "weight", rather its menu system)

---

### Post by TheFu on 2018-03-10
Create a new userid for testing out a new DE -- ZERO risks.  Linux is multi-user. Take advantage of it.  It is handy for troubleshooting all GUI issues, since it removes any personal settings from the issue.

Nobody suggested running 2 DEs concurrently. Run 1 at a time.  Installing just the DE, not all the "environment" stuff which might include a different word processor or editor or terminal isn't necessary.  It is just storage and when not used, sits on disk.  

FVMW has as many different looks as you can imagine. I can understand that some people don't have any interest in tweaking a theme. That's fine.  It is still available and still working perfectly for anyone who wants it. That flexibility is a main reason I love Linux.

I still don't see any downside for the OP in trying a lighter DE under a different userid. The best that happens is great gaming.  The worst that happens is nothing gets better and removing the packages cleans up everything.

I guess we can agree to disagree.

---

### Post by monkeybrain20122 on 2018-03-10
> **TheFu said:**
> 
I guess we can agree to disagree.

No, don't get me wrong, I am not against installing a light DE if it is your preference or if there is a need (say your hardware limitation or certain games don't play nice with 3D desktops etc) But sometimes people just tell others to "switch to a light DE" without even trying to investigate the underlying problems, they automatically assume that problems arise because of 'bloat" which I would venture to say is a wrong diagnosis 9 out of 10 times for modern hardware. Fact is, except for netbooks any Linux DE is "light" on machines that come with Windows >= Vista.Unless you are running antique, 4G of ram is a bare minimum today, "bloat" is a non problem for any Linux DE (something like Windows 10 is a different story altogether)

This attitude contributes to the myth that you somehow need a supercomputer to run something like unity and functional Linux has to be butt ugly or retro looking.  But you can have modern, beautiful and fast Linux desktop, having the best of all worlds. 

In this case for example, OP's main issue is that he has installed a buggy mesa prerelease, switching to a light desktop would have completely missed the point (which might help if OP reinstall Lubuntu or openbox since the driver's bug may then not be exposed by trying to render 3D desktop, but it has nothing to do with it being light perse and it only conceals a problem which can be solved easily)

---

