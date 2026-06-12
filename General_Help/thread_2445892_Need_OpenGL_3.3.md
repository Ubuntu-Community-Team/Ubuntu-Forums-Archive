---
title: "Need OpenGL 3.3"
date: 2020-06-21
forum: General Help
---

### Post by Autodave on 2020-06-21
I am wanting to install OBS onto a system.  The docs on their website state that OpenGL 3.3 is required.  My system is showing OpenGL 3.2.  How / where can I update to 3.3?

---

### Post by Impavidus on 2020-06-21
Upgrade your graphics driver and/or kernel. That is, assuming your hardware actually supports OpenGL 3.3. If not, upgrade that.

---

### Post by Yellow Pasque on 2020-06-21
You didn't even tell us what GPU you have..
```
glxinfo -B
```

---

### Post by Autodave on 2020-06-21
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
Memory info (GL_NVX_gpu_memory_info):
    Dedicated video memory: 8192 MB
    Total available memory: 8192 MB
    Currently available dedicated video memory: 7769 MB
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce RTX 2070/PCIe/SSE2
OpenGL core profile version string: 4.6.0 NVIDIA 440.64
OpenGL core profile shading language version string: 4.60 NVIDIA
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile

OpenGL version string: 4.6.0 NVIDIA 440.64
OpenGL shading language version string: 4.60 NVIDIA
OpenGL context flags: (none)
OpenGL profile mask: (none)

OpenGL ES profile version string: OpenGL ES 3.2 NVIDIA 440.64
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20


I believe that driver is the latest and greatest.

---

### Post by Yellow Pasque on 2020-06-21
> OpenGL version string: 4.6.0 NVIDIA 440.64

You have OpenGL 4.6. You are getting confused and looking at OpenGL ES version. Please mark thread SOLVED

---

### Post by Autodave on 2020-06-21
Thank you!

---

