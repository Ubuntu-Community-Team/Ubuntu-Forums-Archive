---
title: "After updating to Xubuntu 24.10, WebGL no longer works on Firefox (v. 131.03.03) due"
date: 2024-10-25
forum: General Help
---

### Post by vimot2 on 2024-10-25
After updating to Xubuntu 24.10 from 24.04, WebGL no longer works on Firefox (v. 131.03.03), while it works fine in Chrome. 

In about:support I see: 

Driver Informations WSI WebGL 1 - Renderer driver WebGL 1 WebGL creation failed: 

  WebglAllowWindowsNativeGl:false restricts context creation on this system. ()
  Exhausted GL driver options. (FEATURE_FAILURE_WEBGL_EXHAUSTED_DRIVERS)
Renderer driver WebGL 2 WebGL creation failed: 

  AllowWebgl2:false restricts context creation on this system. ()
webgl.enable-prototype-webgl2 is set to true webgl.force is set to true webgl.osmesalib is set to true 



Wayland has not yet been implemented on Xubuntu, so I am still using X11. 

I have the same issue even when running Firefox in safe mode. 

After a few attempts, it seems the issue is related to the Nvidia drivers. I uninstalled the drivers using the command: 

sudo apt purge nvidia-driver 

rebooted the system (now running with the Nouveau drivers), and the sites with WebGL worked. Then I rebooted into maintenance mode and tried to install the previous drivers, nvidia-driver-535, but it seems they are no longer available in Xubuntu 24.10. In fact, nvidia-driver-560 is installed along with some files from nvidia-driver-535, so the problem reappeared. 

I have an Nvidia GeForce RTX 2070 Super on Xubuntu 24.10


Any suggestions?

---

### Post by 1fallen on 2024-10-25
Was this present in driver-555 or 550?

I'm currently testing a rc565 driver and when it finally gets released it might help then. The no wayland issue begs a bug-report on the nVidia driver.

I am on wayland mine looks like:
```
WebGL 1 Driver WSI Info    outOfProcess: false
inProcess: true
EGL_VENDOR: Mesa Project
EGL_VERSION: 1.5
EGL_EXTENSIONS: EGL_EXT_buffer_age EGL_EXT_config_select_group EGL_EXT_create_context_robustness EGL_EXT_present_opaque EGL_EXT_query_reset_notification_strategy EGL_EXT_surface_compression EGL_EXT_swap_buffers_with_damage EGL_KHR_cl_event2 EGL_KHR_config_attribs EGL_KHR_context_flush_control EGL_KHR_create_context EGL_KHR_create_context_no_error EGL_KHR_fence_sync EGL_KHR_get_all_proc_addresses EGL_KHR_gl_colorspace EGL_KHR_gl_renderbuffer_image EGL_KHR_gl_texture_2D_image EGL_KHR_gl_texture_3D_image EGL_KHR_gl_texture_cubemap_image EGL_KHR_image_base EGL_KHR_no_config_context EGL_KHR_reusable_sync EGL_KHR_surfaceless_context EGL_KHR_swap_buffers_with_damage EGL_EXT_pixel_format_float EGL_KHR_wait_sync EGL_MESA_configless_context EGL_MESA_drm_image EGL_MESA_query_driver EGL_MESA_x11_native_visual_id 
EGL_EXTENSIONS(nullptr): EGL_EXT_platform_base EGL_EXT_device_base EGL_EXT_device_enumeration EGL_EXT_device_query EGL_KHR_client_get_all_proc_addresses EGL_EXT_client_extensions EGL_KHR_debug EGL_KHR_platform_x11 EGL_EXT_platform_x11 EGL_EXT_platform_device EGL_MESA_platform_surfaceless EGL_EXT_explicit_device EGL_KHR_platform_wayland EGL_EXT_platform_wayland EGL_KHR_platform_gbm EGL_MESA_platform_gbm EGL_EXT_platform_xcb
WebGL 1 Driver Renderer    Mesa -- llvmpipe (LLVM 18.1.8, 256 bits)
```
```
WebGL 1 Driver Version    4.5 (Compatibility Profile) Mesa 24.2.5-cachyos1.2
WebGL 1 Driver Extensions    GL_ARB_multisample GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_copy_texture GL_EXT_subtexture GL_EXT_texture_object GL_EXT_vertex_array GL_EXT_compiled_vertex_array GL_EXT_texture GL_EXT_texture3D GL_IBM_rasterpos_clip GL_ARB_point_parameters GL_EXT_draw_range_elements GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_separate_specular_color GL_EXT_texture_edge_clamp GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_ARB_framebuffer_sRGB GL_ARB_multitexture GL_EXT_framebuffer_sRGB GL_IBM_multimode_draw_arrays GL_IBM_texture_mirrored_repeat GL_3DFX_texture_compression_FXT1 GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_transpose_matrix GL_EXT_blend_func_separate GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_secondary_color GL_EXT_texture_env_add GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_INGR_blend_func_separate GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texgen_reflection GL_NV_texture_env_combine4 GL_S3_s3tc GL_SUN_multi_draw_arrays GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_EXT_framebuffer_object GL_EXT_texture_compression_s3tc GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_MESA_window_pos GL_NV_packed_depth_stencil GL_NV_texture_rectangle GL_ARB_depth_texture GL_ARB_occlusion_query GL_ARB_shadow GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_window_pos GL_ATI_fragment_shader GL_EXT_stencil_two_side GL_EXT_texture_cube_map GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fog_distance GL_NV_half_float GL_APPLE_packed_pixels GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_shader GL_ARB_shader_objects GL_ARB_vertex_program GL_ARB_vertex_shader GL_ATI_draw_buffers GL_ATI_texture_env_combine3 GL_ATI_texture_float GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_NV_primitive_restart GL_ARB_depth_clamp GL_ARB_fragment_program_shadow GL_ARB_half_float_pixel GL_ARB_occlusion_query2 GL_ARB_point_sprite GL_ARB_shading_language_100 GL_ARB_sync GL_ARB_texture_non_power_of_two GL_ARB_vertex_buffer_object GL_ATI_blend_equation_separate GL_EXT_blend_equation_separate GL_OES_read_format GL_ARB_color_buffer_float GL_ARB_pixel_buffer_object GL_ARB_texture_compression_rgtc GL_ARB_texture_float GL_ARB_texture_rectangle GL_ATI_texture_compression_3dc GL_EXT_packed_float GL_EXT_pixel_buffer_object GL_EXT_texture_compression_dxt1 GL_EXT_texture_compression_rgtc GL_EXT_texture_mirror_clamp GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_texture_shared_exponent GL_ARB_framebuffer_object GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_packed_depth_stencil GL_ARB_vertex_array_object GL_ATI_separate_stencil GL_ATI_texture_mirror_once GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_gpu_program_parameters GL_EXT_gpu_shader4 GL_EXT_texture_array GL_EXT_texture_compression_latc GL_EXT_texture_integer GL_EXT_texture_sRGB_decode GL_EXT_timer_query GL_OES_EGL_image GL_EXT_texture_buffer_object GL_AMD_texture_texture4 GL_ARB_copy_buffer GL_ARB_depth_buffer_float GL_ARB_draw_instanced GL_ARB_half_float_vertex GL_ARB_instanced_arrays GL_ARB_map_buffer_range GL_ARB_texture_buffer_object GL_ARB_texture_rg GL_ARB_texture_swizzle GL_ARB_vertex_array_bgra GL_EXT_texture_swizzle GL_EXT_vertex_array_bgra GL_NV_conditional_render GL_AMD_conservative_depth GL_AMD_draw_buffers_blend GL_AMD_seamless_cubemap_per_texture GL_AMD_shader_stencil_export GL_ARB_ES2_compatibility GL_ARB_blend_func_extended GL_ARB_compatibility GL_ARB_debug_output GL_ARB_draw_buffers_blend GL_ARB_draw_elements_base_vertex GL_ARB_explicit_attrib_location GL_ARB_fragment_coord_conventions GL_ARB_provoking_vertex GL_ARB_sample_shading GL_ARB_sampler_objects GL_ARB_seamless_cube_map GL_ARB_shader_stencil_export GL_ARB_shader_texture_lod GL_ARB_tessellation_shader GL_ARB_texture_buffer_object_rgb32 GL_ARB_texture_cube_map_array GL_ARB_texture_gather GL_ARB_texture_multisample GL_ARB_texture_query_lod GL_ARB_texture_rgb10_a2ui GL_ARB_uniform_buffer_object GL_ARB_vertex_type_2_10_10_10_rev GL_ATI_meminfo GL_EXT_provoking_vertex GL_EXT_texture_snorm GL_EXT_texture_storage GL_MESA_texture_signed_rgba GL_NV_copy_image GL_NV_texture_barrier GL_ARB_draw_indirect GL_ARB_get_program_binary GL_ARB_gpu_shader5 GL_ARB_gpu_shader_fp64 GL_ARB_robustness GL_ARB_separate_shader_objects GL_ARB_shader_bit_encoding GL_ARB_shader_precision GL_ARB_shader_subroutine GL_ARB_texture_compression_bptc GL_ARB_timer_query GL_ARB_transform_feedback2 GL_ARB_transform_feedback3 GL_ARB_vertex_attrib_64bit GL_ARB_viewport_array GL_EXT_direct_state_access GL_EXT_vertex_attrib_64bit GL_AMD_multi_draw_indirect GL_ANGLE_texture_compression_dxt3 GL_ANGLE_texture_compression_dxt5 GL_ARB_base_instance GL_ARB_compressed_texture_pixel_storage GL_ARB_conservative_depth GL_ARB_internalformat_query GL_ARB_map_buffer_alignment GL_ARB_shader_atomic_counters GL_ARB_shader_image_load_store GL_ARB_shading_language_420pack GL_ARB_shading_language_packing GL_ARB_texture_storage GL_ARB_transform_feedback_instanced GL_EXT_framebuffer_multisample_blit_scaled GL_EXT_transform_feedback GL_AMD_query_buffer_object GL_AMD_shader_trinary_minmax GL_AMD_vertex_shader_layer GL_AMD_vertex_shader_viewport_index GL_ARB_ES3_compatibility GL_ARB_arrays_of_arrays GL_ARB_clear_buffer_object GL_ARB_compute_shader GL_ARB_copy_image GL_ARB_explicit_uniform_location GL_ARB_fragment_layer_viewport GL_ARB_framebuffer_no_attachments GL_ARB_invalidate_subdata GL_ARB_multi_draw_indirect GL_ARB_program_interface_query GL_ARB_robust_buffer_access_behavior GL_ARB_shader_image_size GL_ARB_shader_storage_buffer_object GL_ARB_stencil_texturing GL_ARB_texture_buffer_range GL_ARB_texture_query_levels GL_ARB_texture_storage_multisample GL_ARB_texture_view GL_ARB_vertex_attrib_binding GL_KHR_debug GL_KHR_robustness GL_KHR_texture_compression_astc_ldr GL_NV_shader_atomic_float GL_AMD_pinned_memory GL_ARB_buffer_storage GL_ARB_clear_texture GL_ARB_enhanced_layouts GL_ARB_indirect_parameters GL_ARB_internalformat_query2 GL_ARB_multi_bind GL_ARB_query_buffer_object GL_ARB_seamless_cubemap_per_texture GL_ARB_shader_draw_parameters GL_ARB_shader_group_vote GL_ARB_shading_language_include GL_ARB_texture_mirror_clamp_to_edge GL_ARB_texture_stencil8 GL_ARB_vertex_type_10f_11f_11f_rev GL_EXT_debug_label GL_EXT_shader_framebuffer_fetch GL_EXT_shader_integer_mix GL_NVX_gpu_memory_info GL_ARB_ES3_1_compatibility GL_ARB_clip_control GL_ARB_conditional_render_inverted GL_ARB_cull_distance GL_ARB_derivative_control GL_ARB_direct_state_access GL_ARB_get_texture_sub_image GL_ARB_pipeline_statistics_query GL_ARB_shader_texture_image_samples GL_ARB_texture_barrier GL_ARB_transform_feedback_overflow_query GL_ARM_shader_framebuffer_fetch_depth_stencil GL_EXT_polygon_offset_clamp GL_EXT_shader_image_load_formatted GL_KHR_blend_equation_advanced GL_KHR_blend_equation_advanced_coherent GL_KHR_context_flush_control GL_KHR_robust_buffer_access_behavior GL_ARB_ES3_2_compatibility GL_ARB_gpu_shader_int64 GL_ARB_parallel_shader_compile GL_ARB_post_depth_coverage GL_ARB_shader_atomic_counter_ops GL_ARB_shader_ballot GL_ARB_shader_clock GL_ARB_shader_viewport_layer_array GL_ARB_texture_filter_minmax GL_EXT_texture_filter_minmax GL_EXT_texture_sRGB_R8 GL_EXT_texture_sRGB_RG8 GL_KHR_no_error GL_KHR_texture_compression_astc_sliced_3d GL_ARB_gl_spirv GL_ARB_spirv_extensions GL_MESA_shader_integer_functions GL_ARB_polygon_offset_clamp GL_ARB_texture_filter_anisotropic GL_EXT_memory_object GL_EXT_memory_object_fd GL_KHR_parallel_shader_compile GL_EXT_EGL_image_storage GL_EXT_shader_framebuffer_fetch_non_coherent GL_EXT_texture_shadow_lod GL_INTEL_shader_atomic_float_minmax GL_MESA_framebuffer_flip_y GL_EXT_EGL_sync GL_EXT_EGL_image_storage_compression GL_NV_ES1_1_compatibility 
WebGL 1 Extensions    ANGLE_instanced_arrays EXT_blend_minmax EXT_color_buffer_half_float EXT_depth_clamp EXT_float_blend EXT_frag_depth EXT_shader_texture_lod EXT_sRGB EXT_texture_compression_bptc EXT_texture_compression_rgtc EXT_texture_filter_anisotropic MOZ_debug OES_element_index_uint OES_fbo_render_mipmap OES_standard_derivatives OES_texture_float OES_texture_float_linear OES_texture_half_float OES_texture_half_float_linear OES_vertex_array_object WEBGL_color_buffer_float WEBGL_compressed_texture_astc WEBGL_compressed_texture_etc WEBGL_compressed_texture_s3tc WEBGL_compressed_texture_s3tc_srgb WEBGL_debug_renderer_info WEBGL_debug_shaders WEBGL_depth_texture WEBGL_draw_buffers WEBGL_lose_context
```
With this driver:
```
[FONT=monospace][COLOR=#000000]Fri Oct 25 10:01:51 2024        [/COLOR]
+-----------------------------------------------------------------------------------------+ 
| NVIDIA-SMI 565.57.01              Driver Version: 565.57.01      CUDA Version: 12.7     | 
|-----------------------------------------+------------------------+----------------------+ 
| GPU  Name                 Persistence-M | Bus-Id          Disp.A | Volatile Uncorr. ECC | 
| Fan  Temp   Perf          Pwr:Usage/Cap |           Memory-Usage | GPU-Util  Compute M. | 
|                                         |                        |               MIG M. | 
|=========================================+========================+======================| 
|   0  NVIDIA GeForce RTX 3050 ...    Off |   00000000:01:00.0  On |                  N/A | 
| N/A   33C    P8              4W /   60W |     580MiB /   4096MiB |     18%      Default | 
|                                         |                        |                  N/A | 
+-----------------------------------------+------------------------+----------------------+ 
                                                                                          
+-----------------------------------------------------------------------------------------+ 
| Processes:                                                                              | 
|  GPU   GI   CI        PID   Type   Process name                              GPU Memory | 
|        ID   ID                                                               Usage      | 
|=========================================================================================| 
|    0   N/A  N/A      3176      G   /usr/bin/kwalletd6                              1MiB | 
|    0   N/A  N/A      3287      G   /usr/bin/Xwayland                              62MiB | 
|    0   N/A  N/A      3319      G   /usr/bin/ksmserver                              1MiB | 
|    0   N/A  N/A      3321      G   /usr/bin/kded6                                  1MiB | 
|    0   N/A  N/A      3348      G   /usr/bin/plasmashell                           85MiB | 
|    0   N/A  N/A      3358      G   /usr/lib/kactivitymanagerd                      1MiB | 
|    0   N/A  N/A      3364      G   /usr/bin/gmenudbusmenuproxy                     1MiB | 
|    0   N/A  N/A      3365      G   /usr/bin/kaccess                                1MiB | 
|    0   N/A  N/A      3368      G   /usr/lib/xdg-desktop-portal-kde                 1MiB | 
|    0   N/A  N/A      3369      G   /usr/bin/xembedsniproxy                         1MiB | 
|    0   N/A  N/A      3505      G   /usr/bin/kdeconnectd                            1MiB | 
|    0   N/A  N/A      3562      G   /usr/bin/xwaylandvideobridge                    1MiB | 
|    0   N/A  N/A      3577      G   /usr/lib/DiscoverNotifier                       1MiB | 
|    0   N/A  N/A      7799      G   /usr/lib/baloorunner                            1MiB | 
|    0   N/A  N/A     59091      G   /usr/bin/dolphin                                1MiB | 
|    0   N/A  N/A    388418      G   /usr/bin/konsole                                1MiB | 
+-----------------------------------------------------------------------------------------+ 
[COLOR=#54FF54]**&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>**[/COLOR]
[COLOR=#000000] [/COLOR]

[/FONT]
```

---

### Post by 1fallen on 2024-10-25
This is all related to Firefox as snap, it wont see or use your nVidia GPU.
This post is from 25.04 Plucky and all is good here, Xubuntu
```
WebGL 1 Driver Renderer    NVIDIA Corporation -- NVIDIA GeForce RTX 3050 Ti Laptop GPU/PCIe/SSE2
WebGL 1 Driver Version    4.6.0 NVIDIA 560.35.03
```
```
cat /etc/os-release
PRETTY_NAME="Ubuntu Plucky Puffin (development branch)"
NAME="Ubuntu"
VERSION_ID="25.04"
VERSION="25.04 (Plucky Puffin)"
VERSION_CODENAME=plucky
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=plucky
LOGO=ubuntu-logo

```
```
apt policy firefox
firefox:
  Installed: 131.0.3~build1
  Candidate: 131.0.3~build1
  Version table:
  [s]   1:1snap1-0ubuntu6 -1
        500 http://us.archive.ubuntu.com/ubuntu plucky/main amd64 Packages
     131.0.3+build1-0ubuntu0.24.04.1~mt1 500
        500 https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu noble/main amd64 Packages[/s]
 *** 131.0.3~build1 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
        100 /var/lib/dpkg/status
     131.0.2~build1 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     131.0~build1 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     130.0.1~build1 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     130.0~build2 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     129.0.2~build1 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     129.0.1~build1 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     129.0~build2 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     128.0.3~build1 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     128.0.2~build1 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     128.0~build2 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     127.0.2~build1 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     127.0.1~build1 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     127.0~build2 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     126.0.1~build1 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     126.0~build2 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     125.0.3~build1 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     125.0.2~build1 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     125.0.1~build1 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     124.0.2~build1 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     124.0.1~build1 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     124.0~build1 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     123.0.1~build1 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     123.0~build3 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     122.0.1~build1 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     122.0~build2 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
```

---

