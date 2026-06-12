---
title: "[SOLVED] Nvidia driver won't install"
date: 2007-09-18
forum: General Help
---

### Post by smmalis on 2007-09-18
I have tried everything I can think of, but the nvidia driver won't work properly.  I have installed nvidia-glx-new and changed my xconfig for it, I have downloaded the installer from Nvidia and tried it multiple times, nothing works.  I have an 8800 GTS, which is supposed to be supported.  Also, the restricted drivers manager doesn't think that I need any restricted drivers, which obviously isn't true.  PLEASE HELP, I'M DESPERATE!!!

---

### Post by w4ett on 2007-09-18
There are three ways to install the restricted drivers for your card:

1. Use the restricted drivers manager in Ubuntu, System.>Administration>Restricted Driver Manager.[COLOR="Blue"] (try this option first)[/COLOR]

2. Use an installation script called Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) ( this is MY preferred method because it uses the most up to date driver)

3. Compile your own driver modules from Nvidia: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

To use Envy,  navigate to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type:


```
sudo envy -t
```

This will run the installation script from the terminal....follow the instructions to  install the correct Nvidia proprietary driver.

Good Luck

---

### Post by smmalis on 2007-09-19
ok, I installed envy and ran it (used the graphical interface) and no errors.  However, I can't turn on desktop effects, which is what I am using as my test to see if the driver is working. Is the driver really working or what?

---

### Post by w4ett on 2007-09-19
```
glxinfo
```

Will give you the status of your direct rendering (3D)
```

glxgears
```

Will give you relative framerate.

---

### Post by smmalis on 2007-09-19
Check this out:
```
steven@steven-ubuntu:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x3a 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
steven@steven-ubuntu:~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

```

---

### Post by w4ett on 2007-09-19
TSelliot ( the Envy Dev) answered on drivers for your card:

[http://ubuntuforums.org/showthread.php?t=542719](http://ubuntuforums.org/showthread.php?t=542719)

---

### Post by smmalis on 2007-09-19
THANK YOU!!!! I ran envy in recovery mode and now IT WORKS!!!!! THANKS!!!!!!!!

---

### Post by w4ett on 2007-09-19
Super...glad it worked out.....Please mark your thread "Solved"

---

