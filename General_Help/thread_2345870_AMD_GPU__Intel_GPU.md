---
title: "AMD GPU / Intel GPU"
date: 2016-12-08
forum: General Help
---

### Post by Blackbug on 2016-12-08
Hello,

I am using ubuntu 16.10 on HP ultrabook with AMD 7600M and Intel 3000 series GPU.  I am working with caffe opencl framework and I want to use my GPU for the same.

When i run glxinfo it gives me the following info:

```
OpenGL vendor string: Intel Open Source Technology CenterOpenGL renderer string: Mesa DRI Intel(R) Ivybridge Mobile 
OpenGL core profile version string: 3.3 (Core Profile) Mesa 12.0.3
OpenGL core profile shading language version string: 3.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 12.0.3
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.0 Mesa 12.0.3
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.00
OpenGL ES profile extensions:



```

While running Caffe it gives an error as it cannot find the gpu core. How can I check if ubuntu has even installed the AMD GPU driver or my GPUs are available for the use?

I checked for kernel logs they appear to be ok

```
$ dmesg | egrep 'drm|radeon'[    3.375262] [drm] Initialized
[    3.416295] [drm] radeon kernel modesetting enabled.
[    3.416708] [drm] Memory usable by graphics device = 2048M
[    3.416711] fb: switching to inteldrmfb from EFI VGA
[    3.416824] [drm] Replacing VGA console driver
[    3.422875] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    3.422876] [drm] Driver supports precise vblank timestamp query.
[    3.423891] radeon 0000:01:00.0: enabling device (0000 -> 0003)
[    3.424135] [drm] initializing kernel modesetting (TURKS 0x1002:0x6840 0x103C:0x1895 0x00).
[    3.424152] [drm] register mmio base: 0xC0000000
[    3.424153] [drm] register mmio size: 131072
[    3.449523] radeon 0000:01:00.0: VRAM: 2048M 0x0000000000000000 - 0x000000007FFFFFFF (2048M used)
[    3.449525] radeon 0000:01:00.0: GTT: 1024M 0x0000000080000000 - 0x00000000BFFFFFFF
[    3.449530] [drm] Detected VRAM RAM=2048M, BAR=256M
[    3.449531] [drm] RAM width 128bits DDR
[    3.449612] [drm] radeon: 2048M of VRAM memory ready
[    3.449612] [drm] radeon: 1024M of GTT memory ready.
[    3.449622] [drm] Loading TURKS Microcode
[    3.449701] [drm] Internal thermal controller with fan control
[    3.451971] [drm] radeon: dpm initialized
[    3.452055] [drm] GART: num cpu pages 262144, num gpu pages 262144
[    3.452593] [drm] PCIE gen 2 link speeds already enabled
[    3.458635] [drm] PCIE GART of 1024M enabled (table at 0x0000000000162000).
[    3.458741] radeon 0000:01:00.0: WB enabled
[    3.458743] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000080000c00 and cpu addr 0xffff9f7e8c552c00
[    3.458744] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000080000c0c and cpu addr 0xffff9f7e8c552c0c
[    3.459027] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000072118 and cpu addr 0xffffb2c501432118
[    3.459028] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    3.459029] [drm] Driver supports precise vblank timestamp query.
[    3.459030] radeon 0000:01:00.0: radeon: MSI limited to 32-bit
[    3.459064] radeon 0000:01:00.0: radeon: using MSI.
[    3.459098] [drm] radeon: irq initialized.
[    3.475576] [drm] ring test on 0 succeeded in 1 usecs
[    3.475582] [drm] ring test on 3 succeeded in 3 usecs
[    3.651599] [drm] ring test on 5 succeeded in 1 usecs
[    3.651606] [drm] UVD initialized successfully.
[    3.651866] [drm] ib test on ring 0 succeeded in 0 usecs
[    3.651961] [drm] ib test on ring 3 succeeded in 0 usecs
[    4.327711] [drm] ib test on ring 5 succeeded
[    4.330954] [drm] Radeon Display Connectors
[    4.340830] [drm] Initialized radeon 2.48.0 20080528 for 0000:01:00.0 on minor 1
[    4.346351] [drm] Initialized i915 1.6.0 20160919 for 0000:00:02.0 on minor 0
[    4.468959] fbcon: inteldrmfb (fb0) is primary device
[    5.321565] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device



```

---

### Post by ajgreeny on 2016-12-08
That hardware will at the moment be using the open source radeon driver as AMD's current proprietary drivers are not usable with the kernels and xorg versions in use in 16.04 and 16.10.

Regrettably there is nothing that you can do at present to change this, though I believe that AMD are working hard on the fglrx and AMDGPU drivers which will at some point become open-sourced.

It is many years since I have used an AMD/ATI GPU and at the end of my time doing so the fglrx had already become unusable on my hardware and the radeon driver did a fine job for my needs.  These days things may have changed from that situation.

---

