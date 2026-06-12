---
title: "unity 3d not working on samsung nc108???"
date: 2012-10-30
forum: General Help
---

### Post by wangblagak on 2012-10-30
hi, I am new in ubuntu.
as subject, I just installed ubuntu 12.04 on my samsung nc108, but unfortunately desktop cube rotation can't work on it. then I try to find some solutions on many ubuntu forums and still nothing. the important thing that I know is the unity 3d not supported on my netbook.
please help me. you know, for me, ubuntu without compiz is nothing. :-)

sorry my bad english.

---

### Post by Frogs Hair on 2012-10-30
Hello and Welcome 

Recheck Unity 3D support with the following command.```
/usr/lib/nux/unity_support_test -p
``` The Compiz Configuration Settings Manager(CCSM) requires a 3D driver support in order to use the included effects such as the cube.

AFAIK the cube can't be used in 2D. If the support test says you have 3D support then you will want to check Additional Drivers, install the recommended driver and CCSM.

---

### Post by wangblagak on 2012-10-30
> **Frogs Hair said:**
> Hello and Welcome 

Recheck Unity 3D support with the following command.```
/usr/lib/nux/unity_support_test -p
``` The Compiz Configuration Settings Manager(CCSM) requires a 3D driver support in order to use the included effects such as the cube.

AFAIK the cube can't be used in 2D. If the support test says you have 3D support then you will want to check Additional Drivers, install the recommended driver and CCSM.


hi, here is the result.
```

~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string: VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x300)
OpenGL version string: 2.1 Mesa 8.0.2

Not software rendered: no
Not blacklisted: yes
GLX fbconfig: yes
GLX texture from pixmap: yes
GL npot or rect textures: yes
GL vertex program: yes
GL fragment program: yes
GL vertex buffer object: yes
GL framebuffer object: yes
GL version is 1.4+: yes

Unity 3D supported: no
:~$ echo $DESKTOP_SESSION
ubuntu-2d

```

so what do you think?
is there any solution?

---

### Post by Frogs Hair on 2012-10-30
I think you are out of luck though you may want to check additional drivers just in case there is a 3D driver available.

---

### Post by wangblagak on 2012-10-30
> **Frogs Hair said:**
> I think you are out of luck though you may want to check additional drivers just in case there is a 3D driver available.
how to get 3D vga driver for this netbook?

---

### Post by wangblagak on 2012-10-31
what about if I try to switch to GNOME3?

---

### Post by Linuxisfast on 2012-10-31
Unity wont be possible if you are doing VM Ware but try the latest VM Ware via their ppa.

---

### Post by wangblagak on 2012-10-31
> **Linuxisfast said:**
> Unity wont be possible if you are doing VM Ware but try the latest VM Ware via their ppa.
how to do it?

---

