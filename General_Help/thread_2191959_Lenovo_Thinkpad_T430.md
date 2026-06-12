---
title: "Lenovo Thinkpad T430"
date: 2013-12-05
forum: General Help
---

### Post by ebunders on 2013-12-05
Hi

I just bought a lenovo thinkpad T430, and something is not right. When I run /usr/lib/nux/unity_support_test -p I see:
OpenGL vendor string:   Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Ivybridge Mobile 
OpenGL version string:  3.0 Mesa 9.2.1

Looks cool, but when i run glxinfo:
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4

and when I run globs (gl open benchmark suite), and try to run the test ''GLSL_parallax", I get the error "OpenGl 2 not supported!"

So the unity support thest thinks we have opengl version 3,
but other tools indicate I am at version 1.4

When I tried to play a 3d game through steam framerate was 1 :-(
Perhaps the game was not sutable for my Intel HD Graphics 4000, but 1, come on!
So I think something is wrong.

Could anybody help out?

---

