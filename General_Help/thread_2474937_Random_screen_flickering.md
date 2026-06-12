---
title: "Random screen flickering"
date: 2022-05-11
forum: General Help
---

### Post by XargonWan on 2022-05-11
Greetings,


my Ubuntu system is suffering from screen flickering as you can see in this [Video]("https://photos.app.goo.gl/2o2Md5AFqeNfGSz7A").
I tried both the open source and the closed source nvidia drivers but the issue appears with both.
The symptom appears to be random, how can I solve this issue?

I runed a glmark2 but it tested only the integrated intel card, however I post its logs:

```
=======================================================
    glmark2 2021.02
=======================================================
    OpenGL Information
    GL_VENDOR:     Intel
    GL_RENDERER:   Mesa Intel(R) HD Graphics 530 (SKL GT2)
    GL_VERSION:    4.6 (Compatibility Profile) Mesa 22.0.1
=======================================================
[build] use-vbo=false: FPS: 2773 FrameTime: 0.361 ms
[build] use-vbo=true: FPS: 3179 FrameTime: 0.315 ms
[texture] texture-filter=nearest: FPS: 2826 FrameTime: 0.354 ms
[texture] texture-filter=linear: FPS: 2827 FrameTime: 0.354 ms
[texture] texture-filter=mipmap: FPS: 2829 FrameTime: 0.353 ms
[shading] shading=gouraud: FPS: 2703 FrameTime: 0.370 ms
[shading] shading=blinn-phong-inf: FPS: 2717 FrameTime: 0.368 ms
[shading] shading=phong: FPS: 2581 FrameTime: 0.387 ms
[shading] shading=cel: FPS: 2531 FrameTime: 0.395 ms
[bump] bump-render=high-poly: FPS: 1962 FrameTime: 0.510 ms
[bump] bump-render=normals: FPS: 3100 FrameTime: 0.323 ms
[bump] bump-render=height: FPS: 3012 FrameTime: 0.332 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 1917 FrameTime: 0.522 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 1060 FrameTime: 0.943 ms
[pulsar] light=false:quads=5:texture=false: FPS: 2669 FrameTime: 0.375 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 1015 FrameTime: 0.985 ms
[desktop] effect=shadow:windows=4: FPS: 1644 FrameTime: 0.608 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 602 FrameTime: 1.661 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 833 FrameTime: 1.200 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 641 FrameTime: 1.560 ms
[ideas] speed=duration: FPS: 2390 FrameTime: 0.418 ms
[jellyfish] <default>: FPS: 1870 FrameTime: 0.535 ms
[terrain] <default>: FPS: 240 FrameTime: 4.167 ms
[shadow] <default>: FPS: 1826 FrameTime: 0.548 ms
[refract] <default>: FPS: 372 FrameTime: 2.688 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 2494 FrameTime: 0.401 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 2508 FrameTime: 0.399 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 2499 FrameTime: 0.400 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 2494 FrameTime: 0.401 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 2565 FrameTime: 0.390 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 2518 FrameTime: 0.397 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 2525 FrameTime: 0.396 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 2545 FrameTime: 0.393 ms
=======================================================
                                  glmark2 Score: 2129 
=======================================================
```

Here is my neofetch, if you need more information please ask.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290431&stc=1[/IMG]


Thanks in advance

EDIT: moreover sometimes the screen become black for a few seconds (2-8 seconds), not sure if related.

---

### Post by T.J. on 2022-05-14
Hi! 

I use Debian, but I still might be able to help.  Try disabling PSR if your system has it.  It is usually a boot perimeter.  You will have to do a Google search for more information.

---

