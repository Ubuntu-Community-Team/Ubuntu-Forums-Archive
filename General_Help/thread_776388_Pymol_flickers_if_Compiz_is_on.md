---
title: "Pymol flickers if Compiz is on"
date: 2008-04-30
forum: General Help
---

### Post by tijmz on 2008-04-30
Not sure if this is the right forum to ask, so let me apologize in advance if it's not :)

Today I installed Pymol, but the rendering of the molecules doesn't seem to work when I have the advances desktop effects on. If I turn them off, the program works as it should.

The thing that happens is that the molecule window is flickering on and off if I have Compiz on.

Does anyone have any suggestions in what way I can tweak things to have it work properly?

---

### Post by klange on 2008-04-30
I'm not entirely sure what Pymol is, but I assume it uses OpenGL to render. If you don't have a redirected rendering capable driver (which is pretty much everyone except nVidia users and the DRI2 devs), OpenGL apps will flicker.

---

### Post by tijmz on 2008-04-30
Yes, you're right. The screensaver that use OpenGL show the same behaviour. This is new behaviour for me, so I'm guessing it has to do with the upgrade to Hardy I ran last night. :P

I'll mess around with it some, but you're basically saying it's unfixable until DRI2 arrives?

*Edit: installing xserver-xgl got rid of the flickering, but the 3D rendering in PyMol then became unbearingly slow, so I'll be opting for turning off Compiz anytime I need to do some molecular rendering*

---

### Post by leandromartinez98 on 2008-05-22
I have the same problem. I can set direct rendering to Yes in xorg.conf (option DRI true), and then the compiz effects work just fine. However, OpenGL applications (VMD and Pymol) become unusable. If I set direct rendering to off, I cannot enable desktop effects. My graphic card is simple (GMA X3100), but it can handle quite well the desktop effects. It supports or not the direct rendering? If not, why my desktop effects only work if I set "option DRI true" in xorg.conf? In this case glxinfo says direct rendering is available.
Thanks,
Leandro.

---

### Post by leandromartinez98 on 2008-05-23
I think this is the problem, and apparently it has
no solution yet and will not have so soon.

[https://bugs.launchpad.net/ubuntu/+s...ver/+bug/96991](https://bugs.launchpad.net/ubuntu/+s...ver/+bug/96991)

Nothing to be done for now.

Good explanation here:

[http://hoegsberg.blogspot.com/2007/0...rendering.html](http://hoegsberg.blogspot.com/2007/0...rendering.html)

---

### Post by jocko on 2008-06-03
I guess you guys are using hardy with an ati graphics card with ati's proprietary drivers (fglrx)?

Have you tried turning off video overlay and turning on opengl overlay?
I'm not sure it will work (I still use gutsy on my desktop, in part due to the poor quality of the recent ati drivers), but it may be worth testing.
```
sudo gedit /etc/X11/xorg.conf
```
Add these lines in the "Device" section (or change them if they are already there):```

Option    "VideoOverlay" "off"
Option    "OpenGLOverlay "on"
```
If it doesn't help, just remove the lines or set them back to the way they were before.

And now I have a question for fellow pymol users:
Have anyone figured out how to set pymol to full screen?
For me, the full_screen command just maximizes the window instead of activating true full screen mode.
The window decorations are still there and the window size is limited by the gnome panel.

---

### Post by leandromartinez98 on 2008-06-04
The problem is only for the combination of pymol and compiz (the same thing for simples applications, like 3D chess or even the glxgears test). This is the reason
for these problems (the links above were incorrect, sorry):

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/96991](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/96991)

The thing is that compiz tries to control the rendering, while the
graphic card is doing direct rendering to the screen. So, something
called redirected-direct rendering is needed, but it is not implemented
yet in linux kernels. Therefore, we must wait a little. The good
explanation about this is here:

[http://hoegsberg.blogspot.com/2007/08/redirected-direct-rendering.html](http://hoegsberg.blogspot.com/2007/08/redirected-direct-rendering.html)

---

### Post by leandromartinez98 on 2008-06-16
Some news here on the development of that:

[http://hoegsberg.blogspot.com/search?updated-min=2008-01-01T00%3A00%3A00-05%3A00&updated-max=2009-01-01T00%3A00%3A00-05%3A00&max-results=3](http://hoegsberg.blogspot.com/search?updated-min=2008-01-01T00%3A00%3A00-05%3A00&updated-max=2009-01-01T00%3A00%3A00-05%3A00&max-results=3)

---

