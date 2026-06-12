---
title: "Gx60 terascale + southern island 8650g 8970m"
date: 2021-04-16
forum: General Help
---

### Post by genukie on 2021-04-16
Ok so thus far ive managed to get booting with no black screen or editing of grub by using these bios settings

bios setting
power express disabled
dynamic mode enabled
igpu forced performance
_osc to pci0 enabled
enabled all ports for sb gpp
enabled sb memory reverse

then i went and made some config files


sudo nano _/etc/modprobe.d/amdgpu.conf_ 
paste this in
options amdgpu si_support=1
options amdgpu cik_support=1

sudo nano _/etc/modprobe.d/radeon.conf_

options radeon si_support=0
options radeon cik_support=0

sudo nano [U]/etc/mkinitcpio.conf
[/U]mkinitcpio -P

sudo update-initramfs -u

sudo nano_/etc/mkinitcpio.conf_ [B]
MODULES=(amdgpu radeon)
[/B]**sudo nano _/etc/X11/xorg.conf.d/__20-amdgpu.conf_**
Section "Device"
Identifier "AMD"
Driver "modesetting"
#Option "AccelMethod" "Glamor" #valid options are XAA, EXA and Glamor. Default value varies per-GPU.
#Option "AccelMethod" "XAA" #valid options are XAA, EXA and Glamor. Default value varies per-GPU.
#Option "AccelMethod" "EXA" #valid options are XAA, EXA and Glamor. Default value varies per-GPU.
Option "DRI3" "on" #enable DRI3 instead of the default DRI2-mode
EndSection

reupdated initamfs

rebooted and now the 8970m is detected in amdgpu mode and the 8650g is in radeon mode

running unigine heaven and only the igpu is running still any help?

---

### Post by genukie on 2021-04-17
[B]Update Solved

[/B][B]***Update, succeeded in combining the APU and GPU to work together for best frames
Unigine Heaven at 1920x1080 Ultra settings with 8x anti analising low frames 50fps peak 98fps average betweeb 65-75fps[/B]



 CPU: **AMD A10-5750M APU** with Radeon(tm) HD Graphics   2495MHz MMX+ SSE SSE2 SSE3 SSSE3 SSE41 SSE42 SSE4A SSE5 AVX HTT x4 
GPU: Unknown GPU x1
System memory: 13937 MB
Video memory:  256 MB
**Sync threads:  3**
[B]Async threads: 4
---- Render ---- 
GLRender::GLRender(): Unknown ATI GPU
OpenGL vendor:   AMD
OpenGL renderer: AMD Radeon(TM) HD8970M (PITCAIRN, DRM 3.38.0, 5.8.0-50-generic, LLVM 12.0.0)
OpenGL version:  4.6 (Core Profile) Mesa 21.2.0-devel (git-a165385 2021-04-17 focal-oibaf-ppa)
OpenGL flags:    Core Profile[/B]
Found required GL_ARB_map_buffer_range
Found required GL_ARB_vertex_array_object
Found required GL_ARB_draw_instanced
Found required GL_ARB_draw_elements_base_vertex
Found required GL_ARB_transform_feedback
Found required GL_ARB_half_float_vertex
Found required GL_ARB_half_float_pixel
Found required GL_ARB_framebuffer_object
Found required GL_ARB_texture_multisample
Found required GL_ARB_uniform_buffer_object
Found required GL_ARB_geometry_shader4
Found optional GL_ARB_blend_func_extended
Found optional GL_ARB_tessellation_shader
Found optional GL_ARB_shader_bit_encoding
Found optional GL_ARB_sample_shading
Found optional GL_ARB_compute_shader
Found optional GL_ARB_gpu_shader5
Found optional GL_EXT_texture_compression_s3tc
Found optional GL_ARB_texture_compression_rgtc
Shading language:        4.60
Maximum texture size:    16384
Maximum texture units:   192
**Maximum texture renders: 8**

---- Physics ----
Physics: Multi-threaded

---- PathFind ----
PathFind: Multi-threaded

---

### Post by wildmanne39 on 2021-04-17
Great news genukie, please use the thread tools at the top of the page to mark the thread solved.

Thanks

---

