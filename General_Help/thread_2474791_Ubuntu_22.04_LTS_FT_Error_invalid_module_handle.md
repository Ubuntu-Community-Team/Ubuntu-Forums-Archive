---
title: "Ubuntu 22.04 LTS FT_Error: invalid module handle"
date: 2022-05-08
forum: General Help
---

### Post by lmv26 on 2022-05-08
Every time I try to run anything requiring Freetype  that I build I get the following error, iv saw a few other people with this error so if I can id like to get it resolved so I can know for the future, because of how generic the error is google didn't show me any useful info


Error


```
OpenGL ES 2.x information:
  version: "OpenGL ES 3.1 Mesa 22.0.1"
  shading language version: "OpenGL ES GLSL ES 3.10"
  vendor: "Microsoft Corporation"
  renderer: "D3D12 (NVIDIA GeForce RTX 3080)"
===================================
FT_Error (line 101, code 0x22) : invalid module handle
Segmentation fault
```


Github says its some type of driver issue which doesn't really help me


```  
FT_ERRORDEF_( Invalid_Driver_Handle, 0x22 "invalid module handle" )
```


the same code/app works on other older ubuntu versions I have but not this latest one i tried

---

### Post by Impavidus on 2022-05-09
And I assume you compiled the application yourself on the same Ubuntu version where it refuses to run?

There's one program I made myself that uses freetype, which works, but I'm still on Ubuntu 21.10.

---

