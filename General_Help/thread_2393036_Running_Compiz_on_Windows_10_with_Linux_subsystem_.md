---
title: "Running Compiz on Windows 10 with Linux subsystem using Ubuntu"
date: 2018-05-28
forum: General Help
---

### Post by park3300mit on 2018-05-28
I'm trying to install this program called OpenGraphiti on Windows 10 using Ubuntu.

When I run the program, I get this:
```
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
[CANVAS] Creating FrameBuffer Object 1536x864 ...
[SHADER] Couldn't create shader program !
[RESOURCE] loadShader('convolution', 0x14c95e0, 232, 0x14c8f40, 1675)
[CLOCK] Clock created at (1527546489 s, 573783 us).
[CLOCK] Clock created at (1527546489 s, 574019 us).
[CLOCK] Clock created at (1527546489 s, 574164 us).
[CLOCK] Clock created at (1527546489 s, 574290 us).
[CLOCK] Clock created at (1527546489 s, 574409 us).
[CLOCK] Clock created at (1527546489 s, 574579 us).
[SPACEVIEW] Creating space view ...
[SHADER] Couldn't create shader program !
[RESOURCE] loadShader('icon', 0x14c8c40, 300, 0x14c8b60, 209)
terminate called without an active exception
[SHADER] Uniform 'u_ModelViewProjection' not found !Aborted (core dumped)
```

I think the error was related to the Compiz. So when I ran compiz, this returned:
```
Compiz (opengl) - Fatal: Root visual is not a double buffered GL visual
Segmentation fault (core dumped)
```
What does this mean?? How do I fix this? Thank you in advance.

---

