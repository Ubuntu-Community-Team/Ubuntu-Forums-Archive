---
title: "the opengl version in ubuntu recovery mode different to the regular one"
date: 2018-05-27
forum: General Help
---

### Post by nozz90 on 2018-05-27
I'm using a rather old laptop with Intel integrated graphics (Intel atom n450).
During a regular boot, i type glxinfo | grep version, and the opengl version string is 1.4
Now, when i am in recovery mode the output is

server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.4
    Max core profile version: 3.3
    Max compat profile version: 3.1
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 3.0
OpenGL core profile version string: 3.3 (Core Profile) Mesa 18.2.0-devel
OpenGL core profile shading language version string: 3.30
OpenGL version string: 3.1 Mesa 18.2.0-devel
OpenGL shading language version string: 1.40
OpenGL ES profile version string: OpenGL ES 3.0 Mesa 18.2.0-devel
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.00

How is his? Modern opengl 3.3 is shown.
Does opengl recovery mode use different drivers?
If so, can i use them in my default boot to get opengl 3.3 feature?

EDIT: I found out that Ubuntu was using software rendering in recovery mode.
This can be enabled in a regular boot with "export LIBGL_ALWAYS_SOFTWARE=1"
It enables opengl 3.3 support, but is extremely slow, even with basic applications. :(

---

