---
title: "Unable to compile code that includes osmesa.h"
date: 2007-08-10
forum: General Help
---

### Post by RomanG on 2007-08-10
Hello

I'm unable to compile any code that includes /usr/include/GL/osmesa.h under Ubuntu 7.04.

The error messages I get are the following:

In file included from ostest1.c:16:
/usr/include/GL/osmesa.h:119: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘OSMesaContext’
/usr/include/GL/osmesa.h:132: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘OSMesaContext’
/usr/include/GL/osmesa.h:142: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘void’
/usr/include/GL/osmesa.h:174: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLboolean’
/usr/include/GL/osmesa.h:184: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘OSMesaContext’
/usr/include/GL/osmesa.h:202: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘void’
/usr/include/GL/osmesa.h:218: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘void’
/usr/include/GL/osmesa.h:233: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLboolean’
/usr/include/GL/osmesa.h:249: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLboolean’
/usr/include/GL/osmesa.h:266: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘OSMESAproc’
/usr/include/GL/osmesa.h:275: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘void’

Inspecting the preprocessor output using gcc -E reveals that the GLAPI and GLAPIENTRY symbols are not defined:

# 119 "/usr/include/GL/osmesa.h" 3 4
GLAPI OSMesaContext GLAPIENTRY
OSMesaCreateContext( GLenum format, OSMesaContext sharelist );
# 132 "/usr/include/GL/osmesa.h" 3 4
GLAPI OSMesaContext GLAPIENTRY
OSMesaCreateContextExt( GLenum format, GLint depthBits, GLint stencilBits,
                        GLint accumBits, OSMesaContext sharelist);

I have installed the following packages:
$ dpkg -l | grep mesa
ii  libgl1-mesa-dev                            6.5.2-3ubuntu8                             A free implementation of the OpenGL API -- G
ii  libgl1-mesa-dri                            6.5.2-3ubuntu8                             A free implementation of the OpenGL API -- D
ii  libgl1-mesa-glx                            6.5.2-3ubuntu8                             A free implementation of the OpenGL API -- G
ii  libglu1-mesa                               6.5.2-3ubuntu8                             The OpenGL utility library (GLU)
ii  libglu1-mesa-dev                           6.5.2-3ubuntu8                             The OpenGL utility library -- development su
ii  libosmesa6                                 6.5.2-3ubuntu8                             Mesa Off-screen rendering extension
ii  libosmesa6-dev                             6.5.2-3ubuntu8                             Mesa Off-screen rendering extension -- devel
ii  mesa-common-dev                            6.5.2-3ubuntu8                             Developer documentation for Mesa
ii  mesa-utils                                 6.5.2-3ubuntu8                             Miscellaneous Mesa GL utilities
ii  xlibmesa-gl-dev                            7.2-0ubuntu11                              transitional package for Debian etch

Any help is appreciated...

Thanks
-- Roman

---

### Post by RomanG on 2007-08-14
Hello again

I think I found out what causes my problem:

I have installed a graphics drivers using the NVIDIA installer /NVIDIA-Linux-x86-100.14.11-pkg1.run. This installer overwrites the header /usr/include/GL/gl.h with a version that is not compatible with /usr/include/GL/osmesa.h from the libosmesa6-dev package.

Best regards,
Roman

---

