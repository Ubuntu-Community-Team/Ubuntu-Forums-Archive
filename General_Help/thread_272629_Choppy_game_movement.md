---
title: "Choppy game movement"
date: 2006-10-06
forum: General Help
---

### Post by Icon41 on 2006-10-06
okay, I have the latest drivers for my ATI Radeon X800, all games run fine besides graal online, I have had it run in previous ubuntu instalations, but its not working right it moves choppy. I think i might know the problem.

> billy@billy-desktop:~$ graal
Direct Rendering is enabled, Graal should run smoothly.
Processor Init:
   AMD Athlon, 2079 Mhz
   FPU detected
   MMX detected
   3DNow detected
   SSE detected

data directory: /usr/share/graal/
user data directory: /home/billy/.graal/graal4/
Scanning folder structure of /usr/share/graal/...
Scanning folder structure of /home/billy/.graal/graal4/...
Done.
Activating the OpenGL display device (1)...
Setting screen mode to 640x480x32 (w)...
OpenGL Attributes:
  DoubleBuffer: 1
  BufferSize: 32, DepthSize: 24, StencilSize: 0
  Red: 8, Green: 8, Blue: 8, Alpha: 8
  Accum Red: 0, Green: 0, Blue: 0, Alpha: 0
[B]OpenGL driver information:
  Vendor: Mesa project: [www.mesa3d.org](www.mesa3d.org)
  Renderer: Mesa GLX Indirect
  Version: 1.2 (1.5 Mesa 6.4.1)[/B]
OpenGL Init: Enabled Extensions
  ARB_multitexture (Max Texture Units: 8)
  EXT_texture_env_combine
  (ARB|EXT)_texture_env_add
OpenGL Init: Disabled Extensions
  EXT_paletted_texture
  EXT_compiled_vertex_array
  NV_vertex_array_range
  EXT_packed_pixels
  EXT_fog_coord
  ARB_texture_rectangle
  ARB_texture_compression
  EXT_texture_compression_s3tc
  3DFX_texture_compression_FXT1
  EXT_texture_filter_anisotropic
  WGL_EXT_swap_control
  EXT_stencil_two_side
  NV_depth_clamp
  EXT_depth_bounds_test
  EXT_stencil_wrap
  ARB_vertex_blend
  NPatch tessellation

Graal has been activated!


I bolded what I think is the problem, here is my fglrxinfo,
> display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 XL Generic
OpenGL version string: 2.0.5814 (8.25.18)

how could I change graal to run those drivers or something?

---

