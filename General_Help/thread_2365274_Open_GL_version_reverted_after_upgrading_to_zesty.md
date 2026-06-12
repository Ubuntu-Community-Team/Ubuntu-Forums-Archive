---
title: "Open GL version reverted after upgrading to zesty"
date: 2017-07-04
forum: General Help
---

### Post by Patrick_Jeeves on 2017-07-04
Before upgrading to zesty, I could use GLSL 4.5 in programs, but now it tells me that the latest version it supports is 1.3. How do I fix this?

Configuration info:
```

$ sudo lshw -c video | grep 'configuration'
       configuration: driver=amdgpu latency=0
```
```

$ lsmod | grep amdgpu
amdgpu             1564672  26
i2c_algo_bit         16384   1 amdgpu
ttm                  98304   1 amdgpu
drm_kms_helper      151552   1 amdgpu
drm                 352256  13 amdgpu,ttm,drm_kms_helper
```
```

$ glxinfo | grep "version"
server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.4
    Max core profile version: 4.5
    Max compat profile version: 3.0
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 3.1
OpenGL core profile version string: 4.5 (Core Profile) Mesa 17.0.3
OpenGL core profile shading language version string: 4.50
OpenGL version string: 3.0 Mesa 17.0.3
OpenGL shading language version string: 1.30
OpenGL ES profile version string: OpenGL ES 3.1 Mesa 17.0.3
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.10
```

---

