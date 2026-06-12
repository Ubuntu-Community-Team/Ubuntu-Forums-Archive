---
title: "Beryl not working.."
date: 2006-11-20
forum: General Help
---

### Post by Green_Star on 2006-11-20
My Beryl stopped working from couple of days, I do not know how it was happened. Here some info may help you to suggest me the fix.

> :~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300 Series Generic
OpenGL version string: 2.0.6174 (8.31.5)

:~$ glxinfo | grep render
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: Radeon X1300 Series Generic
My xorg.conf file and sources.list files are attached. by the way I didnt get any product updates for Beryl from around ten days? Am I missing something?

Today before I am posting this message I tried installing new drivers using help from **[this page](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#DRI_does_not_work_although_the_fglrx_module_is_loaded)**. I installed 8.31.5 version drivers. Still no luck.

---

### Post by neuroplasma on 2006-11-20
It doesn't look like you have support loaded for direct rendering. Follow the FAQ below to get it working.

[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL)

---

### Post by happy-and-lost on 2006-11-20
AFAIK, Beryl doesn't work in Edgy with ATi cards, as they have to disable composite extensions... at least, I haven't got it working.

---

### Post by strabes on 2006-11-20
right. the same thing happens to me but all seems to work correctly despite that text.

---

### Post by Green_Star on 2006-11-20
I sure that Beryl worked fine after I upgraded to Edgy for couple weeks.

---

### Post by neuroplasma on 2006-11-20
> **happy-and-lost said:**
> AFAIK, Beryl doesn't work in Edgy with ATi cards, as they have to disable composite extensions... at least, I haven't got it working.

I have Beryl running on an x700 with Edgy. I had no problems at all.

---

