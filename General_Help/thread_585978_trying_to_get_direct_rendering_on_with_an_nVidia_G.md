---
title: "trying to get direct rendering on with an nVidia GeForce FX5200"
date: 2007-10-21
forum: General Help
---

### Post by j.miller565 on 2007-10-21
Hi guys and gals. I've just upgraded to Gutsy and now direct rending doesn't seem to work.
I've tried installing the nVidia drivers through Envy, but that too doesn't work.

My card is a nVidia Geforce FX 5200

This is what happens when I type glxinfo | grep direct into the terminal:
```


simon@green-kubuntu-desktop:~$ glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
```


can anyone tell me how I can fix this problem.

Cheers

J.miller565

---

### Post by j.miller565 on 2007-10-21
I fixed it

Just type 

```
sudo apt-get remove xserver-xgl
```

And Direct Rendering works fine now. Compiz Fusion doesn't work anymore but I don't really care  for it as i do for games :)

---

### Post by denis_std on 2007-10-22
it got the same graphics card and the same problem. How could you get 3D desktop AND Nvidia driver running?

---

### Post by Lightstar on 2007-10-22
I've had alot of problems with my FX 5200 not wanting to use any of the compiz effect.. well it kept running in safe mode kinda thing..

i installed nvidia-glx-new

after rebooting the whole desktop and ending up in safemode i made a new xorg.conf

sudo dpkg-reconfigure -phigh xserver-xorg

and added this at the top of the xorg file (put it in your module spot if you already have one).  Open xorg by typing "   sudo gedit /etc/X11/xorg.conf   "



Section "Module"
	Disable		"dbe"
	Disable		"dri"
	Disable		"glx"
	Disable		"vbe"
	Load		"glx"
	Load		"v4l"
EndSection

I don't really know what any of this means, I'm just lucky with the try/error stuff.

That's how i got my nVidia driver to work and Compiz (3D Desktop etc)

My direct rendering is off though, I guess that's the next thing i'll try

---

