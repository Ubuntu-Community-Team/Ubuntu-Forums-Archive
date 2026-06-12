---
title: "cant get direct rendering"
date: 2007-02-25
forum: General Help
---

### Post by hempa on 2007-02-25
Hello! i need some help with getting 3D acceleration to work. i have a ATI Radeon X850 XT graphics card.
i have just installed fglrx. and when i write fglrxinfo in the terminal i get this

armcandy@armcandy-desktop:~$  fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X850 XT Platinum Edition Generic
OpenGL version string: 2.0.6011 (8.28.8

i also wrote glxinfo and it gave me this

armcandy@armcandy-desktop:~$ glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No

---

### Post by Maestro23 on 2007-02-25
See your other post.

---

