---
title: "Compiz check ok"
date: 2008-06-29
forum: General Help
---

### Post by cars1106 on 2008-06-29
Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter
 Driver in use:         sis
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]


I get that from the compiz check.

And i still can't run it. then when I use the icon. it still does not work.

Heres a screen of what happens

[IMG]http://i130.photobucket.com/albums/p252/cars1106/Screenshot.png[/IMG]

I don't know why its doing this. Please Assist me



Heres what happens when I run it in a terminal


kazuma@kazuma-laptop:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

PLease help

---

### Post by psyopper on 2008-06-29
The SIS video cards (all of them to the best of my knowledge) are not capable of running Compiz. You obviously got AIGLX to install properly which is why Compiz-Check thinks you can run Compiz, unfortunately I don't think that card has enough horsepower to actually pull it off...

That said, I may be wrong. That is a pretty old card though.

Consider this a "bug" in compiz-check, maybe? I'm sure Forlong will chime in on this one.

---

### Post by cars1106 on 2008-06-30
Thank you. I guess I need a new laptop. I hate not having the Visual Effects I run windows blinds perfectly with no lag. Blur and all no trouble.

I guess its a linux thing

---

### Post by psyopper on 2008-07-01
Actually it's not a Linux thing, it's a Compiz/OpenGL thing. WindowsBlinds doesn't use your onboard video card with OpenGL to render the screen, WindowsBlinds renders on the processor. Compiz uses OpenGL on your video card to render the screen leaving your processor free to run applications. I actually get lower processor utilization running Compiz than not.

For all intents and purposes, Compiz is an OpenGL "video game" to the likes of Quake III. I have the feeling that if you tried playing QuakeIII in OpenGL mode it would be a slideshow at best on your laptop. I have a laptop like yours (Thinkpad T-22 with an SIS chipset) and I too am crushed that I can not run Compiz on it.

---

