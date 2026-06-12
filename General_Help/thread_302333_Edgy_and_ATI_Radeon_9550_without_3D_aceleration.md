---
title: "Edgy and ATI Radeon 9550 without 3D aceleration"
date: 2006-11-18
forum: General Help
---

### Post by PosTi85 on 2006-11-18
I have a ATI Radeon 9550 on Edgy and I have problems with 'bigs' screensavers, the CPU starts running at 100%. Also, when I type 

$ glxinfo | grep render

I see that I've direct rendering! by when I type:

$ glxgears -printfps

I obtanin:

1247 frames in 5.0 seconds = 249.328 FPS
1103 frames in 5.0 seconds = 220.426 FPS
1248 frames in 5.0 seconds = 249.404 FPS
...

This means that I haven't got 3D acceleration, a Pc with 3D aceleration would show more than 800 FPS. I have used this guide [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide) with the first and method after formating my PC! and then the second one after formating again!

Cedega 3D aceleration test fails... What could I do? Someone with the same problem?

---

### Post by ercerd on 2006-11-20
i had same issue with ati 9550 card but the strange thing when you minimize the gears window i get this fps values
1218 frames in 5.0 seconds = 243.433 FPS
1245 frames in 5.0 seconds = 248.987 FPS
1236 frames in 5.0 seconds = 246.334 FPS
1031 frames in 5.0 seconds = 205.909 FPS
620 frames in 5.0 seconds = 123.995 FPS
614 frames in 5.0 seconds = 122.793 FPS
701 frames in 5.0 seconds = 140.192 FPS
14260 frames in 5.0 seconds = 2851.963 FPS
32867 frames in 5.0 seconds = 6573.279 FPS
32789 frames in 5.0 seconds = 6557.622 FPS
28329 frames in 5.0 seconds = 5665.635 FPS
31800 frames in 5.0 seconds = 6359.913 FPS
30253 frames in 5.0 seconds = 6030.336 FPS
30689 frames in 5.0 seconds = 6137.679 FPS
32607 frames in 5.0 seconds = 6521.303 FPS
27453 frames in 5.0 seconds = 5449.607 FPS
29344 frames in 5.0 seconds = 5868.624 FPS
29310 frames in 5.0 seconds = 5857.393 FPS

and when cedega tests minimize the gears window and all tests passes
> i'm a newbie and this is a strange thing :-D

---

### Post by Ramses de Norre on 2006-11-20
I'm having the same issue with an ati x600, I got way over 2000 fps in dapper but I only get about 300 fps in edgy..

---

### Post by PosTi85 on 2006-11-21
ercerd!!! don't cheat!! ](*,) you must have the window on the front :mrgreen:.

Ramses de Norre, in dapper neither I had problems... I remember that FPS were more! I think that the upgrade has become a problem for our ATI cards... :-k

---

### Post by Fyda on 2006-11-21
Hi, I have this card and am running Edgy, too. In addition, I have Beryl working with the FGLRX driver.

**Running in XGL session (with Beryl):**
Visually, the motion is not smooth, but the framerate is surprisingly high.
> fyda@Tagtraum:~$ glxgears -printfps
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
8352 frames in 5.0 seconds = 1666.728 FPS
8778 frames in 5.0 seconds = 1753.450 FPS
6992 frames in 5.1 seconds = 1381.472 FPS
6954 frames in 5.0 seconds = 1381.587 FPS
6840 frames in 5.5 seconds = 1243.587 FPS
8321 frames in 5.0 seconds = 1652.404 FPS
9006 frames in 5.0 seconds = 1785.218 FPS
9006 frames in 5.0 seconds = 1797.371 FPS
8841 frames in 5.0 seconds = 1754.952 FPS
9120 frames in 5.0 seconds = 1810.295 FPS

**Running in normal GNOME session (without Beryl):**
Opposite of the above. The animation runs very smoothly (perfectly), yet the framerate is much lower!
> fyda@Tagtraum:~$ glxgears -printfps
1251 frames in 5.0 seconds = 250.130 FPS
1250 frames in 5.0 seconds = 249.991 FPS
1250 frames in 5.0 seconds = 249.989 FPS
1248 frames in 5.0 seconds = 249.589 FPS
1250 frames in 5.0 seconds = 249.989 FPS
1250 frames in 5.0 seconds = 249.990 FPS
1250 frames in 5.0 seconds = 249.989 FPS
1250 frames in 5.0 seconds = 249.988 FPS
1250 frames in 5.0 seconds = 249.990 FPS
1250 frames in 5.0 seconds = 249.989 FPS

I remember running glxgears in Dapper (Ubuntu 6.06) without 3D acceleration enabled. Visually it was *very* jerky and the terminal output showed FPS in two digits. :O

Yet, in spite of these numerical differences, OpenGL still performs just fine for me in plain GNOME (it won't work well/at all under XGL, but that is a well-known issue). So I don't judge the performance by the FPS, but by assessing how smoothly it performs.

---

### Post by PosTi85 on 2006-11-22
I don't understand, with Gnome session you get arround 250 FPS (me too... may be the new version of Gnome Desktop :-k in dapper ran fine) but with XGL yo get more! XGL don't use something of the Gnome desktop????

(so in XGL game could work xD WTF?)

---

### Post by Fyda on 2006-11-23
It is strange and I don't understand that either. I would wonder if anyone can explain why this is. I know that XGL currently works as a nested server inside an Xorg server, so 3D acceleration doesn't *appear* to work inside it (but, 3D accel *does* work and is being used by XGL...), but that's about it.

No, lots of 3D games *do not* work in XGL. They only work in regular GNOME. This is why you should install XGL as a session -- so you can switch to GNOME for programs that require 3D acceleration. (This is not because *GNOME* in particular is most game-friendly -- basically, it's just XGL that causes this problem. Anything *other* than XGL should work, eg. OpenBox.)

(At the Spanish Ubuntu community, [this post](http://www.ubuntu-es.org/index.php?q=node/28589#comment-65106) -- see items #3 and #4 -- says the same.)

---

### Post by fuoco on 2006-11-24
I don't know about the odd behaviour with XGL, but the problem with the driver is very very annoying and it doesn't seem to get fixed even though there are bugs open about it for quite some time...

---

### Post by OceanSoul on 2006-11-26
I have the same problem. I have an ATI Radeon 9600XT and I'm getting 248FPS, with direct rendering. I tried installing Beryl, but when I go to GLX session everything is so ugly... lol It's like if Beryl wasn't working (lol, that's exactly it). And I blamed it on the drivers I had. But I will try changing the session to GLX and see the FPS. 

Thank you.

---

### Post by OceanSoul on 2006-11-26
```
$ glxgears
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
11217 frames in 5.0 seconds = 2238.078 FPS
11172 frames in 5.0 seconds = 2220.792 FPS
11182 frames in 5.0 seconds = 2219.143 FPS
11172 frames in 5.0 seconds = 2222.851 FPS
11172 frames in 5.0 seconds = 2222.083 FPS
10961 frames in 5.0 seconds = 2190.500 FPS
11058 frames in 5.0 seconds = 2191.861 FPS
10944 frames in 5.0 seconds = 2167.874 FPS
11075 frames in 5.0 seconds = 2206.409 FPS
10944 frames in 5.0 seconds = 2175.888 FPS
```

```
$ glxinfo | grep rendering
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No
```

```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 2.0.6174 (8.31.5)

```

Ok, now this is stupid. Really stupid. Everything is so slow, Beryl doesn't even work.

Can any of you help?

Thanks in advance.

---

### Post by PosTi85 on 2006-12-04
UP!

Somebody who hasn't read this thread before knows something?

---

### Post by fuoco on 2006-12-17
I was able to compile newer mesa packages (the 3d driver for r300) manually. This has resulted in glxgears fps raising from 25 to around 850-900 for me. The strange thing is that planet penguin racer gives me only 2.5 fps, hardly playable. I don't know what's up with this thing, but part of it must be related to needing new drivers.

---

