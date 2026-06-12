---
title: "Ubuntu slow/unresponsive since latest release (Maybe GFX card related)"
date: 2008-05-13
forum: General Help
---

### Post by Metalmurphy on 2008-05-13
Since the latest update my ubuntu copy has become a bit unresponsive and slow.

For example when scrolling pages in Firefox it has this huge delay and it freezes a bit some times.

Occasionally windows stop responding (go grey) and then come back. When I minimize or open windows it has a small freeze before it does the action.

I think this might be GFX related, I was using some other drivers that I don't recall right now for my ATI x1600 mobility Radeon, I remember that I installed them after googling some problems I was having with Desktop Effects on the previous ubuntu release, Since the new release I installed the drivers that Ubuntu recommended right from the start.

Any idea if my problem is related to that and how can I fix it?

Thanks in advanced.

---

### Post by Metalmurphy on 2008-05-14
Bump :p

---

### Post by prshah on 2008-05-14
> **Metalmurphy said:**
> Since the latest update my ubuntu copy has become a bit unresponsive and slow.

I think this might be GFX related, 

Output of ```
glxinfo | grep direct
```, please?

---

### Post by Thingymebob on 2008-05-14
Oh why was I not surprised to see you have an ATI card?

I will bet if you type fglrxinfo in a terminal the openGL vendor string will read  Mesa, indicating your ATI driver isnt working properly.

I always follow the guide here for getting ATI cards working [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide")

---

### Post by Metalmurphy on 2008-05-17
Sorry for the late reply, been busy.

You are indeed correct Thingymebob :p

Here's the outputs:
```
metalmurphy@metal-laptop:~$ glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect
metalmurphy@metal-laptop:~$ fglrxinfo
display: :1.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.3)

```

Gonna try that guide now.

---

### Post by Metalmurphy on 2008-05-17
Ok, followed the guide, it's showing up as ATI driver now and with direct rendering enabled but nothing changed. I still have a pretty big delay when scrolling and such.

Any ideas?

---

