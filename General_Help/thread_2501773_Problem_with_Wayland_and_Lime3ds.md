---
title: "Problem with Wayland and Lime3ds"
date: 2024-10-20
forum: General Help
---

### Post by salvador2024 on 2024-10-20
Hi, i have a problem with lime3ds when i run a game with Vulkan support:

```

libEGL warning: did not find extension DRI_IMAGE_DRIVER version 1
_amdgpu_device_initialize: amdgpu_query_info(ACCEL_WORKING) failed (-13)
amdgpu: amdgpu_device_initialize failed.
QEGLPlatformContext: Failed to create context: 3000
QWaylandGLContext: Failed to create the decorations EGLContext. Decorations will not be drawn.
QEGLPlatformContext: Failed to create context: 3009
QWaylandGLContext: Failed to create the decorations EGLContext. Decorations will not be drawn.
WARNING: radv is not a conformant Vulkan implementation, testing use only.
QPixmap::scaled: Pixmap is a null pixmap
WARNING: radv is not a conformant Vulkan implementation, testing use only.
/tmp/.mount_lime3dYK0VWh/AppRun.wrapped: symbol lookup error: /usr/lib/x86_64-linux-gnu/libvulkan_radeon.so: undefined symbol: wl_display_create_queue_with_name

```

This problem doesnt happen with my superadmin account (root) and my user is in the group "video" and "render".

My software:
```

OS: Ubuntu Budgie 24.10 x86_64
Linux salvador-System-Version 6.11.0-8-generic #8-Ubuntu SMP PREEMPT_DYNAMIC Mon Sep 16 13:41:20 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux 

```


 I guess it's a permission problem, but I don't know which. Any idea?

THX

---

