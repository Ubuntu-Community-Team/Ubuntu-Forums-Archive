---
title: "AIGLX very slow, XGL don't work... :("
date: 2007-02-20
forum: General Help
---

### Post by psychok9 on 2007-02-20
I've tryed AIGLX and it's very slow...
Now i try fglrx of Ubuntu Repository and ATi Driver... and the result is always  the same:
i type: beryl and:
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : XGL

Checking Display :1.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1.0


With berylmanager the screen splash white and i cant do anything!
please helpme!
thank you

**With XGL loaded:**
user@computer:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 XT Generic
OpenGL version string: 2.0.6286 (8.33.6)
user@computer:~$ glxinfo | grep render
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: RADEON X800 XT Generic
user@computer:~$
[B]
Naturaly Without XGL loaded:[/B]
direct rendering: Yes
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: RADEON X800 XT Generic

---

### Post by psychok9 on 2007-02-20
No help?

---

### Post by mcduck on 2007-02-20
Beryl packages for Edgy are currently broken, resulting in white screen when using XGL. So most likely your install is fine, we'll just have to wait until the packages are fixed..

---

### Post by psychok9 on 2007-02-20
Yeah, i found an temporaly fix with this script (1st line), but don't work perfectly (i can't change skin of top and bottom bar, if i reload it the white screen come back...).

#!/bin/sh
LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa beryl &
beryl-manager &
emerald &

---

### Post by pljones on 2007-02-21
The proprietry ATI drivers don't support compositing.  You need to disable compositing in xorg.conf to get them to appear in glxinfo.

Of course, that breaks Beryl.
<edit>Sorry, just noticed you've got XGL running not xserver-xorg...</edit>

---

### Post by cdeszaq on 2007-02-21
for better support of this issue, go to the #beryl channel on freenode

---

### Post by psychok9 on 2007-02-22
> **mcduck said:**
> Beryl packages for Edgy are currently broken, resulting in white screen when using XGL. So most likely your install is fine, we'll just have to wait until the packages are fixed..

Today i've received updates, but don't work yet... (svn release).

How i can download previous release?

This is my sources.list for Beryl:
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main
deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main

deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn

---

