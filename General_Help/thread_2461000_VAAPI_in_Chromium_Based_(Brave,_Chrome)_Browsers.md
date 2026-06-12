---
title: "VAAPI in Chromium Based (Brave, Chrome) Browsers"
date: 2021-04-22
forum: General Help
---

### Post by Shibblet on 2021-04-22
For the last couple of days, I have been trying to get my Browser to turn on Video Acceleration.  I currently use Brave, but this problem seems to be in Chrome as well.
I am running Kubuntu 20.04.2, and I have an Nvidia GTX780ti, and a Core i7-3770.  

Out of all of the articles I found, this article seems to have had the best information:  [https://www.linuxuprising.com/2021/01/how-to-enable-hardware-accelerated.html]("https://www.linuxuprising.com/2021/01/how-to-enable-hardware-accelerated.html")

The only problem is, even though the "brave://gpu" screen shows everything is working, it actually is not...

I am really floored here.  Does anyone know how to get this to work?

---

### Post by Yellow Pasque on 2021-04-22
What is output of vainfo?
```
vainfo
```

Note that the 780Ti itself doesn't support accelerated decoding of AV1, VP9, or H.265. The only thing it may help with is H.264. You could try the "h264ify" extension if your system is still having issues decoding newer formats.

---

### Post by Shibblet on 2021-04-22
> **Yellow Pasque said:**
> What is output of vainfo?

This:
```
libva info: VA-API version 1.7.0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/nvidia_drv_video.so
libva info: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit

```

> **Yellow Pasque said:**
> Note that the 780Ti itself doesn't support accelerated decoding of AV1, VP9, or H.265. The only thing it may help with is H.264. You could try the "h264ify" extension if your system is still having issues decoding newer formats.

Yup, I am aware.  That's fine though for what I am doing.

---

### Post by Yellow Pasque on 2021-04-22
You need the vdpau-va-driver package, because the Nvidia driver doesn't support VA-API directly and requires a VDPAU wrapper. It's no longer in Ubuntu's repo (for some reason I can't remember), but you can still find it in PPA's like: [https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-beta/+packages](https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-beta/+packages)

---

### Post by Shibblet on 2021-04-23
> **Yellow Pasque said:**
> You need the vdpau-va-driver package, because the Nvidia driver doesn't support VA-API directly and requires a VDPAU wrapper. It's no longer in Ubuntu's repo (for some reason I can't remember), but you can still find it in PPA's like: [https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-beta/+packages](https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-beta/+packages)

Well, I just installed the vdpau-va-driver, as well as the Chromium Dev build.  Still get software decoding.

This is starting to get infuriating.  What am I missing here?

---

### Post by Yellow Pasque on 2021-04-23
> **Shibblet said:**
> Well, I just installed the vdpau-va-driver, as well as the Chromium Dev build.  Still get software decoding.

This is starting to get infuriating.  What am I missing here?

Give the  output of vainfo and chrome://gpu

---

### Post by Shibblet on 2021-04-23
> **Yellow Pasque said:**
> Give the  output of vainfo and chrome://gpu

Here is chrome://gpu

```
Graphics Feature Status
Canvas: Hardware accelerated
Compositing: Hardware accelerated
Multiple Raster Threads: Enabled
Out-of-process Rasterization: Hardware accelerated
OpenGL: Enabled
Rasterization: Hardware accelerated on all pages
Skia Renderer: Enabled
Video Decode: Hardware accelerated
Vulkan: Disabled
WebGL: Hardware accelerated
WebGL2: Hardware accelerated
Driver Bug Workarounds
adjust_src_dst_region_for_blitframebuffer
clear_uniforms_before_first_program_use
exit_on_context_lost
disabled_extension_GL_KHR_blend_equation_advanced
disabled_extension_GL_KHR_blend_equation_advanced_coherent
Problems Detected
Clear uniforms before first program use on all platforms: 124764, 349137
Applied Workarounds: clear_uniforms_before_first_program_use
Disable KHR_blend_equation_advanced until cc shaders are updated: 661715
Applied Workarounds: disable(GL_KHR_blend_equation_advanced), disable(GL_KHR_blend_equation_advanced_coherent)
Some drivers can't recover after OUT_OF_MEM and context lost: 893177
Applied Workarounds: exit_on_context_lost
adjust src/dst region if blitting pixels outside framebuffer on Linux NVIDIA: 830046
Applied Workarounds: adjust_src_dst_region_for_blitframebuffer
ANGLE Features
allow_compressed_formats (Frontend workarounds): Enabled: true
Allow compressed formats
disable_anisotropic_filtering (Frontend workarounds): Disabled
Disable support for anisotropic filtering
disable_program_binary (Frontend features) anglebug:5007: Disabled
Disable support for GL_OES_get_program_binary
disable_program_caching_for_transform_feedback (Frontend workarounds): Disabled: IsAndroid() && isQualcomm
On some GPUs, program binaries don't contain transform feedback varyings
lose_context_on_out_of_memory (Frontend workarounds): Enabled: true
Some users rely on a lost context notification if a GL_OUT_OF_MEMORY error occurs
scalarize_vec_and_mat_constructor_args (Frontend workarounds) 1165751: Disabled: false
Always rewrite vec/mat constructors to be consistent
sync_framebuffer_bindings_on_tex_image (Frontend workarounds): Disabled: false
On some drivers TexImage sometimes seems to interact with the Framebuffer
add_and_true_to_loop_condition (OpenGL workarounds): Disabled: IsApple() && isIntel
Calculation of loop conditions in for and while loop has bug
adjust_src_dst_region_for_blitframebuffer (OpenGL workarounds) 830046: Enabled: IsLinux() || (IsAndroid() && isNvidia) || (IsWindows() && isNvidia) || (IsApple() && functions->standard == STANDARD_GL_ES)
Many platforms have issues with blitFramebuffer when the parameters are large.
allow_clear_for_robust_resource_init (OpenGL workarounds) 883276: Disabled: IsApple()
Using glClear for robust resource initialization is buggy on some drivers and leads to texture corruption. Default to data uploads except on MacOS where it is very slow.
allow_etc_formats (OpenGL workarounds): Disabled: isIntel && !IsSandyBridge(device) && !IsIvyBridge(device) && !IsHaswell(device)
Enable ETC2/EAC on desktop OpenGL
always_call_use_program_after_link (OpenGL workarounds) 110263: Enabled: true
Always call useProgram after a successful link to avoid a driver bug
avoid_1_bit_alpha_texture_formats (OpenGL workarounds): Disabled: functions->standard == STANDARD_GL_DESKTOP && isAMD
Issue with 1-bit alpha framebuffer formats
avoid_dxt1_srgb_texture_format (OpenGL workarounds): Disabled
Replaces DXT1 sRGB with DXT1 sRGB Alpha as a driver bug workaround.
bind_transform_feedback_buffer_before_bind_buffer_range (OpenGL workarounds) anglebug:5140: Disabled: IsApple()
Bind transform feedback buffers to the generic binding point before calling glBindBufferBase or glBindBufferRange.
clamp_array_access (OpenGL workarounds) anglebug:2978: Disabled: IsAndroid() || isAMD || !functions->hasExtension("GL_KHR_robust_buffer_access_behavior")
Clamp uniform array access to avoid reading invalid memory.
clamp_frag_depth (OpenGL workarounds): Enabled: isNvidia
gl_FragDepth is not clamped correctly when rendering to a floating point depth buffer
clamp_msc_rate (OpenGL workarounds) 1042393: Disabled: IsLinux() && IsWayland()
Some drivers return bogus values for GetMscRate, so we clamp it to 30Hz
clamp_point_size (OpenGL workarounds): Enabled: IsAndroid() || isNvidia
The point size range reported from the API is inconsistent with the actual behavior
clear_to_zero_or_one_broken (OpenGL workarounds) 710443: Disabled: IsApple() && isIntel && GetMacOSVersion() < OSVersion(10, 12, 6)
Clears when the clear color is all zeros or ones do not work.
clip_src_region_for_blitframebuffer (OpenGL workarounds) 830046: Disabled: IsApple() || (IsLinux() && isAMD)
Issues with blitFramebuffer when the parameters don't match the framebuffer size.
decode_encode_srgb_for_generatemipmap (OpenGL workarounds) anglebug:4646: Disabled: IsApple()
Decode and encode before generateMipmap for srgb format textures.
disable_blend_func_extended (OpenGL workarounds) anglebug:1085: Disabled: isAMD || isIntel
ARB_blend_func_extended does not pass the tests
disable_draw_buffers_indexed (OpenGL workarounds): Disabled: IsWindows() && isAMD
Disable OES_draw_buffers_indexed extension.
disable_gpu_switching_support (OpenGL workarounds) 1091824: Disabled: isDualGPUMacWithNVIDIA
Disable GPU switching support (use only the low-power GPU) on older MacBook Pros.
disable_native_parallel_compile (OpenGL workarounds) 1094869: Disabled: isTSANBuild && IsLinux() && isNvidia
Do not use native KHR_parallel_shader_compile even when available.
disable_semaphore_fd (OpenGL workarounds) 1046462: Disabled: IsLinux() && isAMD && isMesa && mesaVersion < (std::array<int, 3>{19, 3, 5})
Disable GL_EXT_semaphore_fd extension
disable_sync_control_support (OpenGL workarounds) 1137851: Disabled: false
Speculative fix for issues on Linux/Wayland where exposing GLX_OML_sync_control renders Chrome unusable
disable_timestamp_queries (OpenGL workarounds) 811661: Disabled: IsLinux() && isVMWare
Disable GL_EXT_disjoint_timer_query extension
disable_worker_contexts (OpenGL workarounds) 849576: Enabled: (IsWindows() && (isIntel || isAMD)) || (IsLinux() && isNvidia) || IsIOS()
Some tests have been seen to fail using worker contexts
do_while_glsl_causes_gpu_hang (OpenGL workarounds) 644669: Disabled: IsApple() && functions->standard == STANDARD_GL_DESKTOP && GetMacOSVersion() < OSVersion(10, 11, 0)
Some GLSL constructs involving do-while loops cause GPU hangs
does_srgb_clears_on_linear_framebuffer_attachments (OpenGL workarounds): Disabled: functions->standard == STANDARD_GL_DESKTOP && (isIntel || isAMD)
Issue clearing framebuffers with linear attachments when GL_FRAMEBUFFER_SRGB is enabled
dont_initialize_uninitialized_locals (OpenGL workarounds) anglebug:2046: Disabled: IsAndroid() && isQualcomm
Initializing uninitialized locals caused odd behavior in a few WebGL 2 tests
dont_relink_programs_in_parallel (OpenGL workarounds) anglebug:3045: Disabled: IsAndroid() || (IsWindows() && isIntel)
Relinking a program in parallel is buggy
dont_use_loops_to_initialize_variables (OpenGL workarounds) 809422: Disabled: (IsAndroid() && isQualcomm) || (isIntel && IsApple())
For loops used to initialize variables hit native GLSL compiler bugs
emulate_abs_int_function (OpenGL workarounds) 642227: Disabled: IsApple() && isIntel
abs(i) where i is an integer returns unexpected result
emulate_atan_2_float (OpenGL workarounds) 672380: Enabled: isNvidia
atan(y, x) may return a wrong answer
emulate_copyteximage2d_from_renderbuffers (OpenGL workarounds) anglebug:4674: Disabled: IsApple() && functions->standard == STANDARD_GL_ES && !(isAMD && IsWindows())
CopyTexImage2D spuriously returns errors on iOS when copying from renderbuffers.
emulate_isnan_float (OpenGL workarounds) 650547: Disabled: isIntel && IsApple() && IsSkylake(device) && GetMacOSVersion() < OSVersion(10, 13, 2)
Using isnan() on highp float will get wrong answer
emulate_max_vertex_attrib_stride (OpenGL workarounds) anglebug:1936: Disabled: IsLinux() && functions->standard == STANDARD_GL_DESKTOP && isAMD
Some drivers return 0 when MAX_VERTEX_ATTRIB_STRIED queried
emulate_pack_skip_rows_and_pack_skip_pixels (OpenGL workarounds) anglebug:4849: Disabled: IsApple() && (isAMD || isIntel || isNvidia)
GL_PACK_SKIP_ROWS and GL_PACK_SKIP_PIXELS are ignored in Apple's OpenGL driver.
emulate_primitive_restart_fixed_index (OpenGL workarounds) anglebug:3997: Disabled: functions->standard == STANDARD_GL_DESKTOP && functions->isAtLeastGL(gl::Version(3, 1)) && !functions->isAtLeastGL(gl::Version(4, 3))
When GL_PRIMITIVE_RESTART_FIXED_INDEX is not available, emulate it with GL_PRIMITIVE_RESTART and glPrimitiveRestartIndex.
finish_does_not_cause_queries_to_be_available (OpenGL workarounds): Enabled: functions->standard == STANDARD_GL_DESKTOP && isNvidia
glFinish doesn't cause all queries to report available result
flush_before_delete_texture_if_copied_to (OpenGL workarounds) anglebug:4267: Disabled: IsApple() && isIntel
Some drivers track CopyTex{Sub}Image texture dependencies incorrectly. Flush before glDeleteTextures in this case
init_fragment_output_variables (OpenGL workarounds) 1171371: Disabled: IsAdreno42xOr3xx(functions)
No init gl_FragColor causes context lost
initialize_current_vertex_attributes (OpenGL workarounds): Enabled: isNvidia
During initialization, assign the current vertex attributes to the spec-mandated defaults
keep_buffer_shadow_copy (OpenGL workarounds): Disabled: !CanMapBufferForRead(functions)
Maintain a shadow copy of buffer data when the GL API does not permit reading data back.
max_3d_array_texture_size_1024 (OpenGL workarounds) 927470: Disabled: limitMaxTextureSize
Limit max 3d texture size and max array texture layers to 1024 to avoid system hang
max_msaa_sample_count_4 (OpenGL workarounds) 797243: Disabled: IsAndroid() || (IsApple() && (isIntel || isAMD || isNvidia))
Various rendering bugs have been observed when using higher MSAA counts
max_texture_size_limit_4096 (OpenGL workarounds) 927470: Disabled: IsAndroid() || limitMaxTextureSize
Limit max texture size to 4096 to avoid frequent out-of-memory errors
pack_last_row_separately_for_padding_inclusion (OpenGL workarounds) anglebug:1512: Enabled: IsApple() || isNvidia
When uploading textures from an pack buffer, some drivers count an extra row padding
pack_overlapping_rows_separately_pack_buffer (OpenGL workarounds): Enabled: isNvidia
In the case of packing to a pixel pack buffer, pack overlapping rows row by row
pre_add_texel_fetch_offsets (OpenGL workarounds) 642605: Disabled: IsApple() && isIntel
Intel Mac drivers mistakenly consider the parameter position of nagative vaule as invalid even if the sum of position and offset is in range, so we need to add workarounds by rewriting texelFetchOffset(sampler, position, lod, offset) into texelFetch(sampler, position + offset, lod).
promote_packed_formats_to_8_bit_per_channel (OpenGL workarounds) anglebug:5469: Disabled: IsApple() && hasAMD
Packed color formats are buggy on Macs with AMD GPUs
query_counter_bits_generates_errors (OpenGL workarounds) anglebug:3027: Disabled: IsNexus5X(vendor, device)
Drivers generate errors when querying the number of bits in timer queries
read_pixels_using_implementation_color_read_format (OpenGL workarounds) anglebug:4214: Disabled: functions->standard == STANDARD_GL_ES && functions->isAtLeastGLES(gl::Version(3, 1)) && functions->hasGLESExtension("GL_EXT_texture_norm16")
Quite some OpenGL ES drivers don't implement readPixels for RGBA/UNSIGNED_SHORT from EXT_texture_norm16 correctly
reapply_ubo_bindings_after_using_binary_program (OpenGL workarounds) anglebug:1637: Disabled: isAMD || IsAndroid()
Some drivers forget about UBO bindings when using program binaries
regenerate_struct_names (OpenGL workarounds) 403957: Disabled: IsApple()
All Mac drivers do not handle struct scopes correctly. This workaround overwrites a structname with a unique prefix.
remove_dynamic_indexing_of_swizzled_vector (OpenGL workarounds) 709351: Disabled: IsApple() || IsAndroid() || IsWindows()
Dynamic indexing of swizzled l-values doesn't work correctly on various platforms.
remove_invarient_and_centroid_for_essl3 (OpenGL workarounds): Disabled: functions->isAtMostGL(gl::Version(4, 1)) || (functions->standard == STANDARD_GL_DESKTOP && isAMD)
Fix spec difference between GLSL 4.1 or lower and ESSL3
reset_teximage2d_base_level (OpenGL workarounds) 705865: Disabled: IsApple() && isIntel && GetMacOSVersion() >= OSVersion(10, 12, 4)
Reset texture base level before calling glTexImage2D to work around pixel comparison failure.
reset_texture_generates_errors (OpenGL workarounds) anglebug:3859: Disabled: IsApple() || (IsWindows() && isAMD)
Calling glTexImage2D with zero size generates errors.
rewrite_float_unary_minus_operator (OpenGL workarounds) 308366: Disabled: IsApple() && isIntel && GetMacOSVersion() < OSVersion(10, 12, 0)
Using '-<float>' will get wrong answer
rewrite_repeated_assign_to_swizzled (OpenGL workarounds): Enabled: isNvidia
Repeated assignment to swizzled values inside a GLSL user-defined function have incorrect results
rewrite_row_major_matrices (OpenGL workarounds) anglebug:2273: Disabled: false
Rewrite row major matrices in shaders as column major as a driver bug workaround
rewrite_vector_scalar_arithmetic (OpenGL workarounds) 772651: Enabled: isNvidia
Certain types of GLSL arithmetic ops mixing vectors and scalars may be executed incorrectly
rgb_dxt1_textures_sample_zero_alpha (OpenGL workarounds) anglebug:3729: Disabled: IsApple()
Sampling BLACK texels from RGB DXT1 textures returns transparent black on Mac.
rgba4_is_not_supported_for_color_rendering (OpenGL workarounds): Disabled: functions->standard == STANDARD_GL_DESKTOP && isIntel
GL_RGBA4 is not color renderable
set_primitive_restart_fixed_index_for_draw_arrays (OpenGL workarounds) anglebug:3997: Disabled: features->emulatePrimitiveRestartFixedIndex.enabled && IsApple() && isIntel
Some drivers discard vertex data in DrawArrays calls when the fixed primitive restart index is within the number of primitives being drawn.
set_zero_level_before_generating_mipmap (OpenGL workarounds): Disabled: IsApple()
glGenerateMipmap fails if the zero texture level is not set on some Mac drivers.
unfold_short_circuits (OpenGL workarounds) anglebug:482: Disabled: IsApple()
Mac incorrectly executes both sides of && and || expressions when they should short-circuit.
unpack_last_row_separately_for_padding_inclusion (OpenGL workarounds) anglebug:1512: Enabled: IsApple() || isNvidia
When uploading textures from an unpack buffer, some drivers count an extra row padding
unpack_overlapping_rows_separately_unpack_buffer (OpenGL workarounds): Enabled: isNvidia
In the case of unpacking from a pixel unpack buffer, unpack overlapping rows row by row
unsized_srgb_read_pixels_doesnt_transform (OpenGL workarounds) 565179: Disabled: IsAndroid() && isQualcomm
Drivers returning raw sRGB values instead of linearized values when calling glReadPixels on unsized sRGB texture formats
use_unused_blocks_with_standard_or_shared_layout (OpenGL workarounds): Disabled: (IsApple() && functions->standard == STANDARD_GL_DESKTOP) || (IsLinux() && isAMD)
Unused std140 or shared uniform blocks will be treated as inactive
vertex_id_does_not_include_base_vertex (OpenGL workarounds): Disabled: IsApple() && isAMD
gl_VertexID in GLSL vertex shader doesn't include base vertex value
Version Information
Data exported	2021-04-24T02:43:35.165Z
Chrome version	Chrome/90.0.4430.85
Operating system	Linux 5.8.0-50-generic
Software rendering list URL	https://chromium.googlesource.com/chromium/src/+/5bc145d831c180d9ff94f29a0d7a2e1cbd30ef36/gpu/config/software_rendering_list.json
Driver bug list URL	https://chromium.googlesource.com/chromium/src/+/5bc145d831c180d9ff94f29a0d7a2e1cbd30ef36/gpu/config/gpu_driver_bug_list.json
ANGLE commit id	e22cfa011f5e
2D graphics backend	Skia/90 d9182fe43730b84d59598f460319930eefdaeca7
Command Line	/opt/brave.com/brave/brave --disable-domain-reliability --disable-features=AutofillEnableAccountWalletStorage,AutofillServerCommunication,TextFragmentAnchor,IdleDetection,SignedExchangePrefetchCacheForNavigations,SubresourceWebBundles,WebOTP,NotificationTriggers,LangClientHintHeader,NetworkTimeServiceQuerying,TabHoverCards,DirectSockets,SharingQRCodeGenerator,SignedExchangeSubresourcePrefetch,SafeBrowsingEnhancedProtection,SafeBrowsingEnhancedProtectionMessageInInterstitials,BraveDomainBlock --enable-dom-distiller --enable-features=LegacyTLSEnforced,DnsOverHttps,WebUIDarkMode,ReducedReferrerGranularity,PasswordImport,PrefetchPrivacyChanges,AutoupgradeMixedContent,SafetyTip --extension-content-verification=enforce_strict --extensions-install-verification=enforce --lso-url=https://no-thanks.invalid --no-pings --origin-trial-public-key=bYUKPJoPnCxeNvu72j4EmPuK7tr1PAC7SHh8ld9Mw3E=,fMS4mpO6buLQ/QMd+zJmxzty/VQ6B1EUZqoCU04zoRU= --sync-url=https://sync-v2.brave.com/v2 --variations-server-url=https://variations.brave.com/seed --enable-features=SafetyTip,AutoupgradeMixedContent,PrefetchPrivacyChanges,PasswordImport,ReducedReferrerGranularity,WebUIDarkMode,DnsOverHttps,LegacyTLSEnforced --disable-features=BraveDomainBlock,SafeBrowsingEnhancedProtectionMessageInInterstitials,SafeBrowsingEnhancedProtection,SignedExchangeSubresourcePrefetch,SharingQRCodeGenerator,DirectSockets,TabHoverCards,LangClientHintHeader,NetworkTimeServiceQuerying,NotificationTriggers,WebOTP,SignedExchangePrefetchCacheForNavigations,SubresourceWebBundles,AutofillEnableAccountWalletStorage,AutofillServerCommunication,IdleDetection,TextFragmentAnchor --flag-switches-begin --enable-gpu-rasterization --enable-zero-copy --ignore-gpu-blocklist --enable-features=SafetyTip,AutoupgradeMixedContent,PrefetchPrivacyChanges,PasswordImport,ReducedReferrerGranularity,WebUIDarkMode,DnsOverHttps,LegacyTLSEnforced,VaapiVideoDecoder --flag-switches-end
Driver Information
Initialization time	102
In-process GPU	false
Passthrough Command Decoder	true
Sandboxed	true
GPU0	VENDOR= 0x10de, DEVICE=0x100a *ACTIVE*
GPU1	VENDOR= 0x8086, DEVICE=0x0162
Optimus	true
AMD switchable	false
Driver vendor	Nvidia
Driver version	460.73.01
GPU CUDA compute capability major version	0
Pixel shader version	1.00
Vertex shader version	1.00
Max. MSAA samples	8
Machine model name	
Machine model version	
GL_VENDOR	Google Inc. (NVIDIA Corporation)
GL_RENDERER	ANGLE (NVIDIA Corporation, GeForce GTX 780 Ti/PCIe/SSE2, OpenGL 4.5.0 NVIDIA 460.73.01)
GL_VERSION	OpenGL ES 2.0.0 (ANGLE 2.1.15046 git hash: e22cfa011f5e)
GL_EXTENSIONS	GL_ANGLE_base_vertex_base_instance GL_ANGLE_client_arrays GL_ANGLE_depth_texture GL_ANGLE_explicit_context GL_ANGLE_explicit_context_gles1 GL_ANGLE_framebuffer_blit GL_ANGLE_framebuffer_multisample GL_ANGLE_get_tex_level_parameter GL_ANGLE_instanced_arrays GL_ANGLE_memory_size GL_ANGLE_multi_draw GL_ANGLE_program_cache_control GL_ANGLE_provoking_vertex GL_ANGLE_request_extension GL_ANGLE_robust_client_memory GL_ANGLE_texture_compression_dxt3 GL_ANGLE_texture_compression_dxt5 GL_ANGLE_texture_external_update GL_ANGLE_texture_rectangle GL_ANGLE_translated_shader_source GL_APPLE_clip_distance GL_ARB_sync GL_CHROMIUM_bind_generates_resource GL_CHROMIUM_bind_uniform_location GL_CHROMIUM_color_buffer_float_rgb GL_CHROMIUM_color_buffer_float_rgba GL_CHROMIUM_copy_texture GL_CHROMIUM_lose_context GL_CHROMIUM_sync_query GL_EXT_blend_func_extended GL_EXT_blend_minmax GL_EXT_color_buffer_half_float GL_EXT_debug_label GL_EXT_debug_marker GL_EXT_discard_framebuffer GL_EXT_disjoint_timer_query GL_EXT_draw_buffers GL_EXT_draw_elements_base_vertex GL_EXT_float_blend GL_EXT_frag_depth GL_EXT_gpu_shader5 GL_EXT_instanced_arrays GL_EXT_map_buffer_range GL_EXT_memory_object GL_EXT_memory_object_fd GL_EXT_multisample_compatibility GL_EXT_occlusion_query_boolean GL_EXT_read_format_bgra GL_EXT_robustness GL_EXT_sRGB GL_EXT_sRGB_write_control GL_EXT_semaphore GL_EXT_semaphore_fd GL_EXT_shader_io_blocks GL_EXT_shader_texture_lod GL_EXT_shadow_samplers GL_EXT_texture_buffer GL_EXT_texture_compression_bptc GL_EXT_texture_compression_dxt1 GL_EXT_texture_compression_rgtc GL_EXT_texture_compression_s3tc_srgb GL_EXT_texture_cube_map_array GL_EXT_texture_filter_anisotropic GL_EXT_texture_format_BGRA8888 GL_EXT_texture_rg GL_EXT_texture_sRGB_decode GL_EXT_texture_storage GL_EXT_unpack_subimage GL_KHR_debug GL_KHR_parallel_shader_compile GL_NV_depth_buffer_float2 GL_NV_fence GL_NV_framebuffer_blit GL_NV_pack_subimage GL_NV_pixel_buffer_object GL_NV_read_depth GL_NV_read_stencil GL_NV_robustness_video_memory_purge GL_NV_shader_noperspective_interpolation GL_OES_compressed_EAC_R11_signed_texture GL_OES_compressed_EAC_R11_unsigned_texture GL_OES_compressed_EAC_RG11_signed_texture GL_OES_compressed_EAC_RG11_unsigned_texture GL_OES_compressed_ETC2_RGB8_texture GL_OES_compressed_ETC2_RGBA8_texture GL_OES_compressed_ETC2_punchthroughA_RGBA8_texture GL_OES_compressed_ETC2_punchthroughA_sRGB8_alpha_texture GL_OES_compressed_ETC2_sRGB8_alpha8_texture GL_OES_compressed_ETC2_sRGB8_texture GL_OES_depth24 GL_OES_depth32 GL_OES_depth_texture GL_OES_draw_elements_base_vertex GL_OES_element_index_uint GL_OES_fbo_render_mipmap GL_OES_get_program_binary GL_OES_mapbuffer GL_OES_packed_depth_stencil GL_OES_rgb8_rgba8 GL_OES_shader_image_atomic GL_OES_shader_io_blocks GL_OES_standard_derivatives GL_OES_surfaceless_context GL_OES_texture_3D GL_OES_texture_border_clamp GL_OES_texture_buffer GL_OES_texture_cube_map_array GL_OES_texture_float GL_OES_texture_float_linear GL_OES_texture_half_float GL_OES_texture_half_float_linear GL_OES_texture_npot GL_OES_texture_stencil8 GL_OES_vertex_array_object GL_WEBGL_video_texture
Disabled Extensions	GL_KHR_blend_equation_advanced GL_KHR_blend_equation_advanced_coherent
Disabled WebGL Extensions	
Window system binding vendor	Google Inc. (NVIDIA Corporation)
Window system binding version	1.5 (ANGLE 2.1.15046 git hash: e22cfa011f5e)
Window system binding extensions	EGL_EXT_create_context_robustness EGL_KHR_create_context EGL_KHR_get_all_proc_addresses EGL_ANGLE_create_context_webgl_compatibility EGL_CHROMIUM_create_context_bind_generates_resource EGL_EXT_pixel_format_float EGL_KHR_surfaceless_context EGL_ANGLE_display_texture_share_group EGL_ANGLE_display_semaphore_share_group EGL_ANGLE_create_context_client_arrays EGL_ANGLE_program_cache_control EGL_ANGLE_robust_resource_initialization EGL_ANGLE_create_context_extensions_enabled EGL_ANDROID_blob_cache EGL_ANDROID_recordable EGL_ANGLE_create_context_backwards_compatible EGL_KHR_create_context_no_error EGL_NOK_texture_from_pixmap EGL_NV_robustness_video_memory_purge EGL_KHR_reusable_sync
Window manager	KWin
XDG_CURRENT_DESKTOP	KDE
Compositing manager	Yes
System visual ID	0
RGBA visual ID	0
Direct rendering version	unknown
Reset notification strategy	0x8252
GPU process crash count	0
gfx::BufferFormats supported for allocation and texturing	R_8: not supported, R_16: not supported, RG_88: not supported, BGR_565: not supported, RGBA_4444: not supported, RGBX_8888: not supported, RGBA_8888: not supported, BGRX_8888: not supported, BGRA_1010102: not supported, RGBA_1010102: not supported, BGRA_8888: not supported, RGBA_F16: not supported, YVU_420: not supported, YUV_420_BIPLANAR: not supported, P010: not supported
Compositor Information
Tile Update Mode	Zero-copy
Partial Raster	Enabled
GpuMemoryBuffers Status
R_8	Software only
R_16	Software only
RG_88	Software only
BGR_565	Software only
RGBA_4444	Software only
RGBX_8888	Software only
RGBA_8888	Software only
BGRX_8888	Software only
BGRA_1010102	Software only
RGBA_1010102	Software only
BGRA_8888	Software only
RGBA_F16	Software only
YVU_420	Software only
YUV_420_BIPLANAR	Software only
P010	Software only
Display(s) Information
Info	Display[1] bounds=[0,0 1920x1080], workarea=[0,0 1920x1044], scale=1, rotation=0, panel_rotation=0 external.
Color space (all)	{primaries:BT709, transfer:IEC61966_2_1, matrix:RGB, range:FULL}
Buffer format (all)	BGRA_8888
SDR white level in nits	100
Bits per color component	8
Bits per pixel	24
Refresh Rate in Hz	60
Video Acceleration Information
Vulkan Information
Device Performance Information
```

Here is vainfo:
```
libva info: VA-API version 1.7.0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/nvidia_drv_video.so
libva info: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit

```

---

### Post by Yellow Pasque on 2021-04-25
> vaInitialize failed with error code -1 (unknown libva error),exit

vdpau-va-driver isn't working correctly. I don't know what else to suggest.

---

### Post by Shibblet on 2021-04-25
> **Yellow Pasque said:**
> vdpau-va-driver isn't working correctly. I don't know what else to suggest.

There is an article on this page:  [https://www.linuxuprising.com/2021/01/how-to-enable-hardware-accelerated.html]("https://www.linuxuprising.com/2021/01/how-to-enable-hardware-accelerated.html")

[ATTACH=CONFIG]288372[/ATTACH]

The parts that say [COLOR="#FF0000"]**"from here"**[/COLOR] unfortunately take me to a launchpad login screen that will not accept my launchpad (Ubuntu) credentials.  I can log into Launchpad regularly, but I still cannot pull up those "patched" drivers.

I am pretty sure this patched "vdpau-va-driver" is what I am looking for... but It's behind some kind of wall.

---

### Post by deadflowr on 2021-04-25
Both of the "from here" links should direct you to the ppa archive pages.
Not sure why it's trying to get you to login to launchpad.

---

### Post by Shibblet on 2021-04-26
> **deadflowr said:**
> Both of the "from here" links should direct you to the ppa archive pages.
Not sure why it's trying to get you to login to launchpad.

Yeah, that's the dumbest thing I have encountered in this little attempt... This screenshot is what I was getting.

[ATTACH=CONFIG]288375[/ATTACH]

However, I opened the site with Firefox, instead of Brave, and was able to download the files necessary.

[SIZE=5]New Problem:[/SIZE]

[ATTACH=CONFIG]288376[/ATTACH]

[SIZE=5]Not sure how to satisfy the dependencies here.  Can anyone assist on this?[/SIZE]

**3rd Day Rant:**  This is turning into an outright nightmare...  Why is this so flippin' difficult?  I mean, surely, there are plenty of Linux users out there who have Nvidia Graphics cards who want HW Video Decoding in the Browser?  I really don't know why this is something that has to be built out of legos, and isn't already built into the browser.

**[SIZE=5]UUUUGGGGHHHH!!!![/SIZE]**

On that note...  Shout out to Tony George (teegee2008) for his amazing project "Timeshift."  This has saved me a few times during this annoying escapade.

---

### Post by Yellow Pasque on 2021-04-26
First off, I get that it's frustrating, but don't slaughter our eyes with a bunch of giant fonts. Thanks

>  Why is this so flippin' difficult?

Because Nvidia doesn't support VA-API, and instead, you have to rely on some hacky, old wrapper that's not even maintained anymore. [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=934397](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=934397)

> Not sure how to satisfy the dependencies here.

The problem is that you're taking an individual package that relies on other package versions in the PPA. Don't do that.
If you don't want the whole PPA, then you can try building your own copy (not that difficult): [https://github.com/xtknight/vdpau-va-driver-vp9#compiling](https://github.com/xtknight/vdpau-va-driver-vp9#compiling)
In my experience, 20.04.x already has a recent enough version of libvdpau where you don't have to build your own copy of that, so this should do it:

```
cd ~/ && mkdir source && cd source/
sudo apt-get install build-essential git libvdpau-dev libva-dev libgl-dev
git clone https://github.com/xtknight/vdpau-va-driver-vp9.git
cd vdpau-va-driver-vp9
./autogen.sh --prefix=/usr
make
sudo make install
```

---

### Post by Shibblet on 2021-04-26
> **Yellow Pasque said:**
> First off, I get that it's frustrating, but don't slaughter our eyes with a bunch of giant fonts. Thanks.
It had to be done...

> **Yellow Pasque said:**
> Because Nvidia doesn't support VA-API, and instead, you have to rely on some hacky, old wrapper that's not even maintained anymore. [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=934397](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=934397)
I get it.  It just doesn't need to be so difficult.  This is the 4th day of no-success. It's supposed to be a simple function.  I mean, who doesn't want HW Accelleration for their Browser?  Especially for simple things like video decoding?

> **Yellow Pasque said:**
> The problem is that you're taking an individual package that relies on other package versions in the PPA. Don't do that.
If you don't want the whole PPA, then you can try building your own copy (not that difficult): [https://github.com/xtknight/vdpau-va-driver-vp9#compiling](https://github.com/xtknight/vdpau-va-driver-vp9#compiling)
In my experience, 20.04.x already has a recent enough version of libvdpau where you don't have to build your own copy of that, so this should do it:
I'm all for using a PPA... but there doesn't seem to be one that works.  I have even tried using the Chromium Dev and Chromium Beta build PPA's instead of enabling it for Brave.  That also doesn't work.  I have attempted to follow this guide letter for letter, and nothing seems to work at all.  So, either it's a bad guide, or I am missing something.  And with the number of people saying "Thanks" at the bottom of the guide, I feel like I am missing something.

```
cd ~/ && mkdir source && cd source/
sudo apt-get install build-essential git libvdpau-dev libva-dev libgl-dev
git clone https://github.com/xtknight/vdpau-va-driver-vp9.git
cd vdpau-va-driver-vp9
./autogen.sh --prefix=/usr
make
sudo make install
```[/QUOTE]
Yep... this didn't work either.

I do appreciate all of the help, but it seems as if there is just no way to actually do this.  One of the biggest problems I have always had with Linux in general is this strange attempt at getting "basic" functions working.  It used to be the wireless driver on Laptops... Then they worked that into the Kernel.  Then it was blacklisting Nouveau after installing the Nvidia proprietary driverss so my PC would actually boot.

Over the years, I have grown less interested in "forcing" a computer to do what I need it to... so, to me, the frustration is akin to having a really hot girlfriend who bitches at you all the time.  Yup, she's hot... but look what you have to put up with...

---

### Post by Yellow Pasque on 2021-04-26
> Yep... this didn't work either.

Be more specific. It didn't build? vainfo still fails? What?

---

### Post by Shibblet on 2021-04-26
> **Yellow Pasque said:**
> Be more specific. It didn't build? vainfo still fails? What?

There is an error on launch when I use "brave-browser --use-gl=desktop"  It comes back with "GL is Desktop..."  I forget the rest.

Question though:  I had a friend tell me that HW Acceleration only activates VP9, and not h.264.  Is this true?
If this is the case, I am chasing rainbows here...

---

### Post by Yellow Pasque on 2021-04-26
> brave-browser --use-gl=desktop" It comes back with "GL is Desktop..." I forget the rest.
That is unhelpful. Copy/paste the output.

> Question though: I had a friend tell me that HW Acceleration only activates VP9, and not h.264. Is this true?
Huh? Give a link to what you're talking about.

---

### Post by Shibblet on 2021-04-27
Well, I determined one of the problems.  When trying to add the Chromium-Dev or Chromium-Beta PPA's, Ubuntu is your worst enemy.

Get this...  After adding the PPA, running a "sudo apt update" and also pinning the priority at 1001, you still only download the snap.
I went into Muon to verify this.  The PPA doesn't actually do anything.  The chromium-browser snap takes priority.

And... it get's even better!!!

I am not a big fan of snaps, so I decided to clean out the snap library, and remove snapd from the system.  Also removed the snap program itself.  And tested it by typing "snap list" and got nothing.

However, when I typed in "sudo apt install chromium-browser" after removing snap, and adding the PPA's... Lo and behold chromium-browser goes and installs snap on it's own.
Found this website that verifies exactly what is happening.  Read "Gotcha" at the bottom.

[https://www.kevin-custer.com/blog/disabling-snaps-in-ubuntu-20-04/]("https://www.kevin-custer.com/blog/disabling-snaps-in-ubuntu-20-04/")

Truly, for the first time in my Linux life, I am actually offended by this!  

[LIST=1]
[*]Why in the living heck would a software package install a different installer?
[*]Why would APT install Snaps?  Isn't it a supposed to be a different package manager?
[*]Why can't the new PPA override the old snap package?
[/LIST]

Anyway... that's been my problem.  I kept downloading the Snap of Chromium-Browser, and that's why nothing works.

---

### Post by Shibblet on 2021-04-27
Tried again... this time I get:

vainfo
```

libva info: VA-API version 1.10.0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/nvidia_drv_video.so
libva info: Found init function __vaDriverInit_1_7
libva info: va_openDriver() returns 0
vainfo: VA-API version: 1.10 (libva 2.10.0)
vainfo: Driver version: Splitted-Desktop Systems VDPAU backend for VA-API - 0.7.4
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            : VAEntrypointVLD
      VAProfileMPEG2Main              : VAEntrypointVLD
      VAProfileMPEG4Simple            : VAEntrypointVLD
      VAProfileMPEG4AdvancedSimple    : VAEntrypointVLD
      <unknown profile>               : VAEntrypointVLD
      VAProfileH264Main               : VAEntrypointVLD
      VAProfileH264High               : VAEntrypointVLD
      VAProfileVC1Simple              : VAEntrypointVLD
      VAProfileVC1Main                : VAEntrypointVLD
      VAProfileVC1Advanced            : VAEntrypointVLD

```

and Error message after typing "brave-browser --use-gl=desktop"

```

[12690:12690:0427/183814.363952:ERROR:gpu_init.cc(426)] Passthrough is not supported, GL is desktop
[12663:12663:0427/183814.455173:ERROR:profile_attributes_storage.cc(548)] Failed to PNG encode the image.

```

---

### Post by Yellow Pasque on 2021-04-28
> vainfo
Yeah, that looks good.

> ERROR:gpu_init.cc(426)] Passthrough is not supported, GL is desktop
I don't know what to tell you. I don't get much when I google that. Have you looked at CPU usage when playing an h.264 video to see if there's any difference?

---

### Post by Shibblet on 2021-04-28
> **Yellow Pasque said:**
> I don't know what to tell you. I don't get much when I google that. Have you looked at CPU usage when playing an h.264 video to see if there's any difference?

Doesn't seem to be.

I mean, it's not a major deal.  I can decode 1080p on the CPU with no frame loss, and it all works great.  The problem is, I like to run other apps in the background that utilize the CPU, and I'd like to do other things on my PC like, watch videos, and not have them take CPU cycles away from my other processes.

Ugh... I guess...

This just doesn't seem like it should be such a major problem.

Anyway, thank you very much for the help... even through my side-rants.  ;-)

---

### Post by Yellow Pasque on 2021-04-29
Okay, if using  brave, see: [https://github.com/brave/brave-browser/issues/1024#issuecomment-723425330](https://github.com/brave/brave-browser/issues/1024#issuecomment-723425330)

---

### Post by Shibblet on 2021-05-02
I was finally able to get this to work.  What was happening, is once the "libvdpau1 1.4.2" dependency was installed, Discover would update it to the 1.4.3 driver from the standard repositories... thus overwriting the patched file, and making everything no-workie...

Anyway.  "I re-installed libvdpau1 1.4.2," then went into Muon, and locked that baby down, and now I get Video Acceleration in Brave-Browser.  

I did have to get the Chrome Extension "x264ify" to force YouTube to send H.264 instead of VP9, because my GTX780ti does not support VP9... although it works great with H.264!

My secondary problem now, is Google Stadia.  I have the Stadia Enhanced Extension, that will allow me to force H.264 instead of VP9, but I can only get Stadia to use the Software Decoder.
The Stadia stream monitor shows that it is sending H.264, but only in Software.

[ATTACH=CONFIG]288421[/ATTACH]

Again, I ask if there is any help?

---

### Post by laukokpin on 2021-05-08
Any Luck? I'm trying to get my browser's youtube hardware acceleration working too.

---

### Post by Shibblet on 2021-05-10
> **laukokpin said:**
> Any Luck? I'm trying to get my browser's youtube hardware acceleration working too.

Nope.

I was able to get YouTube acceleration working in Kubuntu 21.04, but not Stadia.

---

### Post by laukokpin on 2021-05-12
My laptop has a nvidia 840m geforce card. I'm trying to get hardware acceleration working for youtube on the browser.


As the cpu heats up. 


After spending much time going through forums and guides. I found out that vdpau is not even enabled.


THe result of vdpauinfo. and vaainfo is bellow.


vdpauinfo
display: :1   screen: 0
GPU at BusId 0x1 doesn't have a supported video decoder
Error creating VDPAU device: 1




vainfo
libva info: VA-API version 1.8.0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/nvidia_drv_video.so
libva info: Found init function __vaDriverInit_1_7
GPU at BusId 0x1 doesn't have a supported video decoder
libva error: /usr/lib/x86_64-linux-gnu/dri/nvidia_drv_video.so init failed
libva info: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit

---

