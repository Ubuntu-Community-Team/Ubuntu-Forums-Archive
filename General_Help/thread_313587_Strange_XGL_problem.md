---
title: "Strange XGL problem"
date: 2006-12-06
forum: General Help
---

### Post by Green_Star on 2006-12-06
My Beryl is running for for couple of months and stopped suddenly, I tried installing drivers and beryl again but no luck, I have XGL is running in different session. I have two different out puts for my drivers info please see below.

In my normal gnome session
> :~$ glxinfo | grep render
direct rendering: Yes
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: Radeon X1300 Series Generic

:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300 Series Generic
OpenGL version string: 2.0.6174 (8.31.5)

In XGL session 
> :~$ glxinfo | grep render
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: Radeon X1300 Series Generic

:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300 Series Generic
OpenGL version string: 2.0.6174 (8.31.5)

Please check my xorg configuration and help me out to fix this issue. I can get you any logs if you need....

thanks in advance.

---

### Post by Green_Star on 2006-12-07
It is another strange that if I do  ***rm ~/.beryl/settings*** then Beryl started working, but once i change any settings in **Beryl Settings Manager**, then again it stops working till I remove that settings.....

---

