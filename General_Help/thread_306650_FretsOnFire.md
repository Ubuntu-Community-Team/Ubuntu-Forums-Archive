---
title: "FretsOnFire"
date: 2006-11-25
forum: General Help
---

### Post by InsomniacUK on 2006-11-25
Can anyone help me get this game running?

[http://louhi.kempele.fi/~skyostil/uv/fretsonfire/](http://louhi.kempele.fi/~skyostil/uv/fretsonfire/)

Works like a charm on Windows, but whenever I try to run the Linux version I get this error;

```
Traceback (most recent call last):
  File "/home/skyostil/src/cx_Freeze-3.0.3/initscripts/Console.py", line 27, in ?
  File "src/FretsOnFire.py", line 61, in ?
  File "src/GameEngine.py", line 166, in __init__
  File "src/Data.py", line 45, in __init__
  File "src/Data.py", line 76, in loadSvgDrawing
  File "src/Svg.py", line 556, in convertToTexture
  File "src/Svg.py", line 108, in getRenderingQuality
AttributeError: GOpenGLBoard instance has no attribute 'RenderingQuality'

```

Can anyone help?

---

### Post by tqft on 2007-01-04
Did you ever get it working - I have a similar problem

---

### Post by mpgarate on 2007-02-18
same problem. anyone? please?

---

### Post by WW on 2007-02-18
Wow, I just tried it out.  The tutorial is hilarious.

I suspect the problem is that you don't have the right libraries installed.  The readme.txt file says you need SDL, SDL_ttf and SDL_mixer.  I have libsdl1.2debian, libsdl1.2debian-oss, libsdl-mixer1.2, and libsdl-ttf2.0-0 installed.  I don't know if these are the packages that you need, but it probably couldn't hurt to try.  If you are using Ubuntu 6.06 (dapper), you can install them with this command:
> $ sudo apt-get install libsdl1.2debian libsdl1.2debian-oss libsdl-mixer1.2 libsdl-ttf2.0-0
If you are using 6.10 (edgy), the version numbers might be different.  Try searching in Synaptic for **sdl mixer**, **sdl ttf** or just **sdl**.

---

