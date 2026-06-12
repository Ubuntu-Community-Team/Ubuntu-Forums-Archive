---
title: "Celestia crashes on startup"
date: 2005-07-30
forum: General Help
---

### Post by spiraloid on 2005-07-30
Radeon 8500. Happens with both the DEB fglrx drivers and the latest ones from the ATI site (version listed below). Happens with all versions of celestia I've tried, deb installation, from source 1.3.2 or from source latest CVS (as of Jul 30/05). Celestia compiled with just a minimal GTK interface, I've also tried GLUT and GNOME.. the GNOME interface crashes before even getting this far, but all the rest (including KDE interface from DEB installation) crash at this exact same place:

```
mike@hst:~/src/celestia-1.3.2$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 8500 DDR Generic
OpenGL version string: 1.3.1003 (X4.3.0-8.14.13)

mike@hst:~/src/celestia-1.3.2$ glxgears
11551 frames in 5.0 seconds = 2310.200 FPS
12242 frames in 5.0 seconds = 2448.400 FPS
12257 frames in 5.0 seconds = 2451.400 FPS
12213 frames in 5.0 seconds = 2442.600 FPS
12258 frames in 5.0 seconds = 2451.600 FPS
mike@hst:~/src/celestia-1.3.2$ fgl_glxgears
1707 frames in 5.0 seconds = 341.400 FPS
1809 frames in 5.0 seconds = 361.800 FPS
1804 frames in 5.0 seconds = 360.800 FPS
1769 frames in 5.0 seconds = 353.800 FPS
1796 frames in 5.0 seconds = 359.200 FPS
mike@hst:~/src/celestia-1.3.2$ /usr/local/bin/celestia
nStars: 112524
Initializing ARB vertex programs . . .
Loading ARB vertex program: shaders/diffuse_arb.vp
Loading ARB vertex program: shaders/specular_arb.vp
Loading ARB vertex program: shaders/haze_arb.vp
Loading ARB vertex program: shaders/bumpdiffuse_arb.vp
Loading ARB vertex program: shaders/bumphaze_arb.vp
Loading ARB vertex program: shaders/shadowtex_arb.vp
Loading ARB vertex program: shaders/diffuse_texoff_arb.vp
Loading ARB vertex program: shaders/rings_arb.vp
Loading ARB vertex program: shaders/ringshadow_arb.vp
Loading ARB vertex program: shaders/night_arb.vp
Loading ARB vertex program: shaders/glossmap_arb.vp
All ARB vertex programs loaded successfully.
render path: 3
Segmentation fault
```

The window flashes open for a second. I'm certainly thinking this has to do with some GL library somewhere. I have run celestia successfully with this card in Linux before but not since I switched to Ubuntu. So what's going on? How can I get more detailed information to try and debug this problem more closely? Other GL apps run fine, such as Alias Maya, Scorched 3D, Blender, you name it.

*edit*: I enabled an option in the config file to ignore ARB extensions, which makes it default to RenderPath 1.. still segfaults, just doesn't do all the loading of ARB vertex programs first. So the problem doesn't lie there.

Mike

---

### Post by spiraloid on 2005-07-30
Some interesting added info.. I ran celestia through GDB, and received this:

```
All ARB vertex programs loaded successfully.
render path: 3

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread -1225381792 (LWP 24248)]
0xb60e0053 in s9425 () from /usr/X11R6/lib/modules/dri/atiogl_a_dri.so
```

So it appears the fault is in the ATI DRI driver. Hmmmm......... still don't know what to do about fixing this though. :-/

---

### Post by Outworlder on 2005-09-19
Got exactly the same problem. I wonder if someone found a solution for it already.

For the record, it worked with the opensource driver (just incredbly slow). When I installed the ATI driver, it stopped working.

---

### Post by leonleyva on 2006-09-18
was this solved...??

I have the same problem... now in Sept 2006!!!!

---

### Post by lfys on 2006-12-18
And indeed I have the same problem after folowing
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

Still no solution?

(If I have no solution by wednesday, my pupils will see me going back tot WinXP! D'oh!)

---

