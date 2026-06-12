---
title: "Blender not working"
date: 2007-11-17
forum: General Help
---

### Post by Qinjuehang on 2007-11-17
I always open my blender in the Terminal, to keep track of rendering progress in Yafray.

Whenever I switch desktop, regardless of desktop wall or desktop cube, I get: DRM_I830_CMDBUFFER: -22

I'm using Intel 845G graphics card, and Pentium 4 without HT. (My computer is OLD)

Anyone who knows what's the problem?

---

### Post by Qinjuehang on 2007-11-21
*bump*

---

### Post by jespdj on 2007-11-22
I guess you are using Ubuntu 7.10?
Which version of Blender are you using?

Instead of Blender 2.44, which is in the Ubuntu repository, get Blender 2.45 from [blender.org](http://www.blender.org/download/get-blender/). It fixes some bugs that make it more stable. Maybe it fixes the problem you're experiencing too.

---

### Post by Qinjuehang on 2007-11-23
Ok I'll try that. Thanks. However, I happen to think it is a problem in the Intel Graphics driver, because I don't think Blender is the only program affected.

---

### Post by Qinjuehang on 2007-11-24
Didn't work :(

---

### Post by Offoffoff on 2007-11-25
I use 01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M wtih xorg-video-ati. Blender (2.44 or 2.45) doesn't work and shows in terminal this:
```
/usr/share$ blender -d
guessing 'blender-bin' == '/usr/bin/blender-bin'
Blender 2.45 (sub 0) Build
argv[0] = blender-bin
argv[1] = -d
Compiled with Python version 2.4.4.
Checking for installed Python... got it!
Color depth r 5 g 6 b 5
Aux buffers: 0
read file 
  Version 242 sub 4
read file 
  Version 241 sub 0

ordered
 OBCube
 OBLamp
 OBCamera

Registering scripts in Blender menus ...

Getting menu data for scripts from file:
/home/worker/.blender/Bpymenus

Color depth r 5 g 6 b 5
Aux buffers: 0
Color depth r 5 g 6 b 5
Aux buffers: 0
Color depth r 5 g 6 b 5
Aux buffers: 0
Color depth r 5 g 6 b 5
Aux buffers: 0
Segmentation fault (core dumped)

```

---

### Post by Qinjuehang on 2007-11-25
I installed xfce, and now whenever I need to use Blender, I use xfce instead of gnome. I think compiz fusion is not even mature enough to be bundled with a operating system...I'm waiting for Hardy

---

