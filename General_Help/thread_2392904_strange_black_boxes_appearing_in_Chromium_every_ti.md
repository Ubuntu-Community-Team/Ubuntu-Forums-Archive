---
title: "strange black boxes appearing in Chromium every time I stroll"
date: 2018-05-26
forum: General Help
---

### Post by ardouronerous on 2018-05-26
sometimes whenever I browse on Chromium, strange black boxes appearing are every time I stroll.
[ATTACH=CONFIG]279875[/ATTACH]

this doesn't happen in Firefox though.

---

### Post by kerry_s on 2018-05-27
it looks like it's not using accelerated graphics.

try going into chrome://flags enable the very top 1

---

### Post by ardouronerous on 2018-05-27
What do you mean by the very top 1? You mean the "Reset all to default?"

---

### Post by kerry_s on 2018-05-27
no, i think it was called override software rendering?

---

### Post by ardouronerous on 2018-05-27
Okay, I've enabled it.
Why was it disabled by default and what are the downsides of enabling it?

---

### Post by ardouronerous on 2018-05-27
The black boxes are still appearing.

---

### Post by kerry_s on 2018-05-27
some vid cards are blacklisted even though most of the features work perfectly fine.

downside would be if it don't work :)

---

### Post by kerry_s on 2018-05-27
check chrome://gpu see what it says.

what is your vid?

---

### Post by ardouronerous on 2018-05-27
[COLOR=#000000][FONT=sans-serif]**Graphics Feature Status**


[LIST]
[*]Canvas: [COLOR=#008000]Hardware accelerated[/COLOR] 
[*]CheckerImaging: [COLOR=#FF0000]Disabled[/COLOR] 
[*]Flash: [COLOR=#008000]Hardware accelerated[/COLOR] 
[*]Flash Stage3D: [COLOR=#008000]Hardware accelerated[/COLOR] 
[*]Flash Stage3D Baseline profile: [COLOR=#008000]Hardware accelerated[/COLOR] 
[*]Compositing: [COLOR=#008000]Hardware accelerated[/COLOR] 
[*]Multiple Raster Threads: [COLOR=#FF0000]Disabled[/COLOR] 
[*]Native GpuMemoryBuffers: [COLOR=#808000]Software only. Hardware acceleration disabled[/COLOR] 
[*]Rasterization: [COLOR=#808000]Software only. Hardware acceleration disabled[/COLOR] 
[*]Surface Synchronization: [COLOR=#008000]Enabled[/COLOR] 
[*]Video Decode: [COLOR=#008000]Hardware accelerated[/COLOR] 
[*]WebGL: [COLOR=#008000]Hardware accelerated[/COLOR] 
[*]WebGL2: [COLOR=#008000]Hardware accelerated[/COLOR] 
[/LIST]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]**Driver Bug Workarounds**


[LIST]
[*]clear_uniforms_before_first_program_use 
[*]count_all_in_varyings_packing 
[*]decode_encode_srgb_for_generatemipmap 
[*]disable_framebuffer_cmaa 
[*]disable_post_sub_buffers_for_onscreen_surfaces 
[*]scalarize_vec_and_mat_constructor_args 
[/LIST]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]**Problems Detected**


[LIST]
[*]Clear uniforms before first program use on all platforms: [124764]("http://crbug.com/124764"), [349137]("http://crbug.com/349137")
*Applied Workarounds: [COLOR=#808000]clear_uniforms_before_first_program_use[/COLOR]* 
[*]Mesa drivers in Linux handle varyings without static use incorrectly: [333885]("http://crbug.com/333885")
*Applied Workarounds: [COLOR=#808000]count_all_in_varyings_packing[/COLOR]* 
[*]Always rewrite vec/mat constructors to be consistent: [398694]("http://crbug.com/398694")
*Applied Workarounds: [COLOR=#808000]scalarize_vec_and_mat_constructor_args[/COLOR]* 
[*]NVIDIA drivers before 346 lack features in NV_path_rendering and related extensions to implement driver level path rendering.: [344330]("http://crbug.com/344330")
*Applied Workarounds: [COLOR=#808000]disable(GL_NV_path_rendering)[/COLOR]* 
[*]Use GL_INTEL_framebuffer_CMAA on ChromeOS: [535198]("http://crbug.com/535198")
*Applied Workarounds: [COLOR=#808000]disable_framebuffer_cmaa[/COLOR]* 
[*]Disable partial swaps on Mesa drivers (detected with GL_VERSION): [339493]("http://crbug.com/339493")
*Applied Workarounds: [COLOR=#808000]disable_post_sub_buffers_for_onscreen_surfaces[/COLOR]* 
[*]Decode and encode before generateMipmap for srgb format textures on os except macosx: [634519]("http://crbug.com/634519")
*Applied Workarounds: [COLOR=#808000]decode_encode_srgb_for_generatemipmap[/COLOR]* 
[*]Disable KHR_blend_equation_advanced until cc shaders are updated: [661715]("http://crbug.com/661715")
*Applied Workarounds: [COLOR=#808000]disable(GL_KHR_blend_equation_advanced)[/COLOR], [COLOR=#808000]disable(GL_KHR_blend_equation_advanced_coherent)[/COLOR]* 
[*]Don't expose disjoint_timer_query extensions to WebGL: [808744]("http://crbug.com/808744") 
[*]Raster is using a single thread.
*Disabled Features: [COLOR=#FF0000]multiple_raster_threads[/COLOR]* 
[*]Native GpuMemoryBuffers have been disabled, either via about:flags or command line.
*Disabled Features: [COLOR=#FF0000]native_gpu_memory_buffers[/COLOR]* 
[*]Checker-imaging has been disabled via finch trial or the command line.
*Disabled Features: [COLOR=#FF0000]checker_imaging[/COLOR]* 
[/LIST]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]**Version Information**

[TABLE="width: 1034"]
[TR]
[TD]**Data exported**[/TD]
[TD]2018-05-27T04:40:08.952Z[/TD]
[/TR]
[TR]
[TD]**Chrome version**[/TD]
[TD]Chrome/66.0.3359.181[/TD]
[/TR]
[TR]
[TD]**Operating system**[/TD]
[TD]Linux 4.4.0-127-generic[/TD]
[/TR]
[TR]
[TD]**Software rendering list URL**[/TD]
[TD]https://chromium.googlesource.com/chromium/src/+/164c37e3f235134c88e80fac2a182cfba3f07f00/gpu/config/software_rendering_list.json[/TD]
[/TR]
[TR]
[TD]**Driver bug list URL**[/TD]
[TD]https://chromium.googlesource.com/chromium/src/+/164c37e3f235134c88e80fac2a182cfba3f07f00/gpu/config/gpu_driver_bug_list.json[/TD]
[/TR]
[TR]
[TD]**ANGLE commit id**[/TD]
[TD]unknown hash[/TD]
[/TR]
[TR]
[TD]**2D graphics backend**[/TD]
[TD]Skia/66 773868fdade5f9f0e7697e6d09c9bd80aaa9b402-[/TD]
[/TR]
[TR]
[TD]**Command Line**[/TD]
[TD]/usr/lib/chromium-browser/chromium-browser --enable-pinch --flag-switches-begin --ignore-gpu-blacklist --flag-switches-end[/TD]
[/TR]
[/TABLE]


[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]**Driver Information**

[TABLE="width: 1034"]
[TR]
[TD]**Initialization time**[/TD]
[TD]187[/TD]
[/TR]
[TR]
[TD]**In-process GPU**[/TD]
[TD]false[/TD]
[/TR]
[TR]
[TD]**Passthrough Command Decoder**[/TD]
[TD]false[/TD]
[/TR]
[TR]
[TD]**Direct Composition**[/TD]
[TD]false[/TD]
[/TR]
[TR]
[TD]**Supports overlays**[/TD]
[TD]false[/TD]
[/TR]
[TR]
[TD]**Sandboxed**[/TD]
[TD]false[/TD]
[/TR]
[TR]
[TD]**GPU0**[/TD]
[TD]VENDOR = 0x10de, DEVICE= 0x0641 *ACTIVE*[/TD]
[/TR]
[TR]
[TD]**Optimus**[/TD]
[TD]false[/TD]
[/TR]
[TR]
[TD]**Optimus**[/TD]
[TD]false[/TD]
[/TR]
[TR]
[TD]**AMD switchable**[/TD]
[TD]false[/TD]
[/TR]
[TR]
[TD]**Driver vendor**[/TD]
[TD]Mesa[/TD]
[/TR]
[TR]
[TD]**Driver version**[/TD]
[TD]17.2.8[/TD]
[/TR]
[TR]
[TD]**Driver date**[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]**Pixel shader version**[/TD]
[TD]1.30[/TD]
[/TR]
[TR]
[TD]**Vertex shader version**[/TD]
[TD]1.30[/TD]
[/TR]
[TR]
[TD]**Max. MSAA samples**[/TD]
[TD]8[/TD]
[/TR]
[TR]
[TD]**Machine model name**[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]**Machine model version**[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]**GL_VENDOR**[/TD]
[TD]nouveau[/TD]
[/TR]
[TR]
[TD]**GL_RENDERER**[/TD]
[TD]NV96[/TD]
[/TR]
[TR]
[TD]**GL_VERSION**[/TD]
[TD]3.0 Mesa 17.2.8[/TD]
[/TR]
[TR]
[TD]**GL_EXTENSIONS**[/TD]
[TD]GL_AMD_conservative_depth GL_AMD_performance_monitor GL_AMD_shader_trinary_minmax GL_ANGLE_texture_compression_dxt3 GL_ANGLE_texture_compression_dxt5 GL_APPLE_packed_pixels GL_ARB_ES2_compatibility GL_ARB_ES3_compatibility GL_ARB_arrays_of_arrays GL_ARB_base_instance GL_ARB_blend_func_extended GL_ARB_buffer_storage GL_ARB_clear_buffer_object GL_ARB_clear_texture GL_ARB_clip_control GL_ARB_color_buffer_float GL_ARB_compressed_texture_pixel_storage GL_ARB_conditional_render_inverted GL_ARB_conservative_depth GL_ARB_copy_buffer GL_ARB_copy_image GL_ARB_cull_distance GL_ARB_debug_output GL_ARB_depth_buffer_float GL_ARB_depth_clamp GL_ARB_depth_texture GL_ARB_derivative_control GL_ARB_draw_buffers GL_ARB_draw_elements_base_vertex GL_ARB_draw_instanced GL_ARB_explicit_attrib_location GL_ARB_explicit_uniform_location GL_ARB_fragment_coord_conventions GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_framebuffer_object GL_ARB_framebuffer_sRGB GL_ARB_get_program_binary GL_ARB_get_texture_sub_image GL_ARB_half_float_pixel GL_ARB_half_float_vertex GL_ARB_instanced_arrays GL_ARB_internalformat_query GL_ARB_internalformat_query2 GL_ARB_invalidate_subdata GL_ARB_map_buffer_alignment GL_ARB_map_buffer_range GL_ARB_multi_bind GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_occlusion_query2 GL_ARB_pipeline_statistics_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_program_interface_query GL_ARB_provoking_vertex GL_ARB_robustness GL_ARB_sampler_objects GL_ARB_seamless_cube_map GL_ARB_separate_shader_objects GL_ARB_shader_bit_encoding GL_ARB_shader_clock GL_ARB_shader_objects GL_ARB_shader_texture_image_samples GL_ARB_shader_texture_lod GL_ARB_shading_language_100 GL_ARB_shading_language_420pack GL_ARB_shading_language_packing GL_ARB_shadow GL_ARB_stencil_texturing GL_ARB_sync GL_ARB_texture_barrier GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_compression_rgtc GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirror_clamp_to_edge GL_ARB_texture_mirrored_repeat GL_ARB_texture_multisample GL_ARB_texture_non_power_of_two GL_ARB_texture_query_levels GL_ARB_texture_rectangle GL_ARB_texture_rg GL_ARB_texture_rgb10_a2ui GL_ARB_texture_stencil8 GL_ARB_texture_storage GL_ARB_texture_storage_multisample GL_ARB_texture_swizzle GL_ARB_texture_view GL_ARB_timer_query GL_ARB_transpose_matrix GL_ARB_uniform_buffer_object GL_ARB_vertex_array_bgra GL_ARB_vertex_array_object GL_ARB_vertex_attrib_binding GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_vertex_type_10f_11f_11f_rev GL_ARB_vertex_type_2_10_10_10_rev GL_ARB_window_pos GL_ATI_blend_equation_separate GL_ATI_draw_buffers GL_ATI_fragment_shader GL_ATI_separate_stencil GL_ATI_texture_compression_3dc GL_ATI_texture_env_combine3 GL_ATI_texture_float GL_ATI_texture_mirror_once GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_copy_texture GL_EXT_depth_bounds_test GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_multisample_blit_scaled GL_EXT_framebuffer_object GL_EXT_framebuffer_sRGB GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_float GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_polygon_offset_clamp GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shader_integer_mix GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_array GL_EXT_texture_compression_dxt1 GL_EXT_texture_compression_latc GL_EXT_texture_compression_rgtc GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_integer GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_texture_sRGB_decode GL_EXT_texture_shared_exponent GL_EXT_texture_snorm GL_EXT_texture_swizzle GL_EXT_timer_query GL_EXT_transform_feedback GL_EXT_vertex_array GL_EXT_vertex_array_bgra GL_EXT_window_rectangles GL_IBM_multimode_draw_arrays GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_KHR_context_flush_control GL_KHR_debug GL_KHR_no_error GL_MESA_pack_invert GL_MESA_shader_integer_functions GL_MESA_texture_signed_rgba GL_MESA_window_pos GL_NV_blend_square GL_NV_conditional_render GL_NV_depth_clamp GL_NV_fog_distance GL_NV_light_max_exponent GL_NV_packed_depth_stencil GL_NV_primitive_restart GL_NV_texgen_reflection GL_NV_texture_barrier GL_NV_texture_env_combine4 GL_NV_texture_rectangle GL_NV_vdpau_interop GL_OES_EGL_image GL_OES_read_format GL_S3_s3tc GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays[/TD]
[/TR]
[TR]
[TD]**Disabled Extensions**[/TD]
[TD]GL_KHR_blend_equation_advanced GL_KHR_blend_equation_advanced_coherent GL_NV_path_rendering[/TD]
[/TR]
[TR]
[TD]**Disabled WebGL Extensions**[/TD]
[TD]EXT_disjoint_timer_query EXT_disjoint_timer_query_webgl2[/TD]
[/TR]
[TR]
[TD]**Window system binding vendor**[/TD]
[TD]SGI[/TD]
[/TR]
[TR]
[TD]**Window system binding version**[/TD]
[TD]1.4[/TD]
[/TR]
[TR]
[TD]**Window system binding extensions**[/TD]
[TD]GLX_ARB_create_context GLX_ARB_create_context_profile GLX_ARB_fbconfig_float GLX_ARB_framebuffer_sRGB GLX_ARB_multisample GLX_EXT_create_context_es_profile GLX_EXT_create_context_es2_profile GLX_EXT_fbconfig_packed_float GLX_EXT_framebuffer_sRGB GLX_EXT_import_context GLX_EXT_texture_from_pixmap GLX_EXT_visual_info GLX_EXT_visual_rating GLX_MESA_copy_sub_buffer GLX_OML_swap_method GLX_SGI_swap_control GLX_SGIS_multisample GLX_SGIX_fbconfig GLX_SGIX_pbuffer GLX_SGIX_visual_select_group GLX_INTEL_swap_event[/TD]
[/TR]
[TR]
[TD]**Window manager**[/TD]
[TD]Openbox[/TD]
[/TR]
[TR]
[TD]**XDG_CURRENT_DESKTOP**[/TD]
[TD]LXDE[/TD]
[/TR]
[TR]
[TD]**GDMSESSION**[/TD]
[TD]Lubuntu[/TD]
[/TR]
[TR]
[TD]**Compositing manager**[/TD]
[TD]No[/TD]
[/TR]
[TR]
[TD]**Direct rendering**[/TD]
[TD]Yes[/TD]
[/TR]
[TR]
[TD]**Reset notification strategy**[/TD]
[TD]0x8261[/TD]
[/TR]
[TR]
[TD]**GPU process crash count**[/TD]
[TD]0[/TD]
[/TR]
[TR]
[TD]**System visual ID**[/TD]
[TD]33[/TD]
[/TR]
[TR]
[TD]**RGBA visual ID**[/TD]
[TD]118[/TD]
[/TR]
[/TABLE]


[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]**Compositor Information**

[TABLE="width: 1034"]
[TR]
[TD]**Tile Update Mode**[/TD]
[TD]One-copy[/TD]
[/TR]
[TR]
[TD]**Partial Raster**[/TD]
[TD]Enabled[/TD]
[/TR]
[/TABLE]


[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]**GpuMemoryBuffers Status**

[TABLE="width: 1034"]
[TR]
[TD]**ATC**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**ATCIA**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**DXT1**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**DXT5**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**ETC1**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**R_8**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**R_16**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**RG_88**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**BGR_565**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**RGBA_4444**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**RGBX_8888**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**RGBA_8888**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**BGRX_8888**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**BGRX_1010102**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**RGBX_1010102**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**BGRA_8888**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**RGBA_F16**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**YVU_420**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**YUV_420_BIPLANAR**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**UYVY_422**[/TD]
[TD]Software only[/TD]
[/TR]
[/TABLE]


[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]**Display(s) Information**

[TABLE="width: 1034"]
[TR]
[TD]**Info**[/TD]
[TD]Display[1657894779767808] bounds=0,0 1600x900, workarea=0,0 1600x900, scale=1, external[/TD]
[/TR]
[TR]
[TD]**Color space information**[/TD]
[TD]{primaries:INVALID, transfer:INVALID, matrix:INVALID, range:INVALID}[/TD]
[/TR]
[TR]
[TD]**Bits per color component**[/TD]
[TD]8[/TD]
[/TR]
[TR]
[TD]**Bits per pixel**[/TD]
[TD]24[/TD]
[/TR]
[/TABLE]


[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]**Video Acceleration Information**



[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]**Log Messages**


[LIST]
[*][8091:8091:0527/123925.969230:ERROR:sandbox_linux.cc(379)] : InitializeSandbox() called with multiple threads in process gpu-process. 
[/LIST]
[/FONT][/COLOR]

---

### Post by kerry_s on 2018-05-27
why aren't you using the driver for your vid card.

---

### Post by ardouronerous on 2018-05-27
I've had some bad experiences using the proprietary driver.
The open source driver seems to work well for me, well, besides from this little hickup.

---

### Post by kerry_s on 2018-05-27
i see. for starters lets try enabling all those disabled for the gpu.
go back into chrome://flags & search "threads" change it to 4 then this-> Multiple Raster Threads: Disabled <- should get enabled

CheckerImaging: Disabled <- there should also be a toggle for this to enable

Native GpuMemoryBuffers: Software only. Hardware acceleration disabled <- this 1 is zero-copy... enable it

Rasterization: Software only. Hardware acceleration disabled <-- i think this 1 is called gpu-rasterization ? enable it

---

### Post by ardouronerous on 2018-05-27
I enabled zero-copy rasterizer and GPU rasterization, but I couldn't find Multiple Raster Threads and CheckerImaging.

---

### Post by kerry_s on 2018-05-27
do it the old fashion way & scroll down, you'll know it when you see them.

---

### Post by ardouronerous on 2018-05-27
Okay, I've set Number of raster threads to 4.

still can't find checkerimage, is it AsyncImageDecoding or Image Capture API?

---

### Post by kerry_s on 2018-05-27
well maybe you don't need it are there still black boxes?

---

### Post by ardouronerous on 2018-05-27
Thanks for the help, I'm experiencing no black boxes right now, I'll continue to monitor thanks.

---

