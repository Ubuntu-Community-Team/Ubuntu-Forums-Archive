---
title: "Clean install-lagging?"
date: 2014-04-20
forum: General Help
---

### Post by matt96 on 2014-04-20
hi
i'm new to ubuntu and installed the 14.04 LTS on my old computer which has

in the system setting it shows 
pentium 4 1.60ghz
1 gb ram
graphic: Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bit)


i thought that was enough
but everything is lagging like when i click on the menu on top right it takes couple seconds to come up and is not smooth
however the mouse arrow is moving smoothly

i installed with a 5gb swap space

is there anything i'm doing wrong?

please help

PS: didn't where to post this sorry if in the wrong section

---

### Post by grahammechanical on 2014-04-20
Gallium 0.4 = Nouveau open source video driver. llvmpipe = a subset of Nouveau that is used by Ubuntu when the video adapter is not powerful enough to run Unity with 3D accelerated graphics. We also get llvmpipe when we run Recovery mode>Resume.

Run

```
/usr/lib/nux/unity_support_test -p
```

this is what I get

> OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NVA5
OpenGL version string:  3.0 Mesa 10.1.0


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


As you can see I am using Nouveau (Gallium) but not on llvmpipe. You could try activating an proprietary video driver. System Settings>Software and Updates>Additional Drivers tab.

Regards

[FONT=Ubuntu Mono]


[/FONT]

---

### Post by matt96 on 2014-04-20
there is nothing in Additional Drivers tab

would a lower version of ubuntu work?

---

