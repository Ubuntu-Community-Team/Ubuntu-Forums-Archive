---
title: "openGL for matlab on breezy"
date: 2005-10-31
forum: General Help
---

### Post by jrb114 on 2005-10-31
Hi,

I'm having a nightmare trying to set up openGL for matlab release 14.

I've got the nvidia drivers working (eventually) for gnome, but I can't get past this problem in matlab.

When I try to run "opengl info" I get:

>> opengl info
Attempting to load glren.so
Warning: Unable to load the OpenGL renderer due to the following error
/usr/local/matlab14/bin/glnx86/../../sys/os/glnx86/libgcc_s.so.1: version `GCC_3.3' not found (required by /usr/lib/libstdc++.so.6)
Tried loading glren shared object from: glren.so
> In opengl at 98
Switching to Software OpenGL Rendering.
Attempting to load glren_mesa.so
Warning: Unable to load the OpenGL renderer due to the following error
/usr/local/matlab14/bin/glnx86/../../sys/os/glnx86/libgcc_s.so.1: version `GCC_3.3' not found (required by /usr/lib/libstdc++.so.6)
Tried loading glren shared object from: glren_mesa.so
> In opengl at 98
Warning: Could not access OpenGL library
> In opengl at 98

====

So it looks like it might be to do with gcc, but I haven't got a clue. (I tried CC=gcc-3.3, export CC, as I needed to do to compile the nvidia driver under breezy (except I used CC=gcc-3.4, ...) but no joy there either.)

If anybody has any ideas, I'd must appreciate them.

NB I couldn't get this to work under Hoary either, but found installing the nvidia drivers much easier on Hoary than Breezy.

Thanks

J

---

### Post by jrb114 on 2005-11-05
Turns out the solution was just to delete the libgcc_s.so.1 from the matlab directory so that it picks up the system one. (Or rather mv libgcc_s.so to libgcc_s.so.old).

Full solution and description from the link below

[http://newsreader.mathworks.com/WebX?14@oEoIaT4fbzc@.ef1a487](http://newsreader.mathworks.com/WebX?14@oEoIaT4fbzc@.ef1a487)

J

---

