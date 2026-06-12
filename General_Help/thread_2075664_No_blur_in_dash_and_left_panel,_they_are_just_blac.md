---
title: "No blur in dash and left panel, they are just black"
date: 2012-10-24
forum: General Help
---

### Post by globulus on 2012-10-24
Hi!
I am using Ubuntu 12.10 on my VMware machine. 
12.04 was just fine, but with 12.10 I am facing several problems.

1) missing amd microcode. Solution is: sudo apt-get install amd64-microcode. But why it is missing???

2) no blur in dash and left panel, they are just black. In CCSM chose Active blur, but no effect has landed. I have no any solution.

[Screenshot of the trouble]("http://flic.kr/p/dnqSSi")

Why it is happening and what I am to do????

---

### Post by globulus on 2012-10-25
nobody answers:confused:

---

### Post by garginis on 2012-10-25
Have you installed graphic card driver?Also, does you graphic card support 3D?

---

### Post by globulus on 2012-10-25
> **garginis said:**
> Have you installed graphic card driver?Also, does you graphic card support 3D?

Off course, I installed graphic card driver, and yes, my graphic card supports 3D.

/usr/lib/nux/unity_support_test -p

```
 
OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on SVGA3D; build: RELEASE;  
OpenGL version string:  2.1 Mesa 9.0

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

```

---

