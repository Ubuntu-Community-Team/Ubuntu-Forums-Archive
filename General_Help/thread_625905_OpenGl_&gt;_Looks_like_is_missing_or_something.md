---
title: "OpenGl &gt; Looks like is missing or something"
date: 2007-11-28
forum: General Help
---

### Post by Dakohn on 2007-11-28
1. Ive been trying to play .exe Games on my PC (such as Tibia) and they all give me the same output:

> X Server has no OpenGL extension. (Error Code 31)

Please ensure your X Server features an OpenGL extension.


So, I now know that the problem has something to do with OpenGL.
I went into the Synaptic Package Manager and installed xserver-xgl which only made things worst once I logged out and back in. I entered my username and pass and the screen halves while loading, I waited 10 seconds and went back to login screen. I entered in Failsafe GNOME and uninstalled xserver-xgl and Im back to normal.

2. Ive also been having problems with Compiz. I went into a Compiz guide of "what do I need to do before installing Compiz". I use an NVidia driver so...Well, the first step was to check the NVida Driver Version with:

> glxinfo | grep "OpenGL version string:"

This should return something like this: 

> OpenGL version string: 2.1.0 NVIDIA 96.31

But instead, it gave me this :confused: :

> dan@dan-pc:/home/Tibia$ glxinfo | grep "OpenGL version string:"
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".


Sooooo...
PLEASE HELP :confused:

---

### Post by skymera on 2007-11-28
have you got the driver installed?

if so how did you install it?

i recommend ENVY, 11/10.

worked perfect every time.

---

### Post by Dakohn on 2007-11-28
Im not sure if it is installed, but I do know its enabled.
System> Administrator> Restricted Drivers Manager

It says its enabled and in use.

---

