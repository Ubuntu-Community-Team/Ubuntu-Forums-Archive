---
title: "help enabling 3d acceleration"
date: 2007-04-05
forum: General Help
---

### Post by cptjaben on 2007-04-05
I'm trying to get Beryl/XGL running on my laptop, but I cannot get 3d acceleration to work. When I type glxinfo | grep direct I get:
```
 glxinfo | grep direct

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

``` 

Also When I type fglrxinfo I get:
```
fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)


``` my laptop has an ATI X1700, I've follow [this]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_1:_Install_the_8.28.8_Driver_the_Ubuntu_Way") guide so far and it hasn't worked, can anyone help me out?

---

### Post by cantormath on 2007-04-05
have you tried envy?
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
for ATI and Nvidia.

---

### Post by cptjaben on 2007-04-06
Awesome, it worked really well. Thanks

---

