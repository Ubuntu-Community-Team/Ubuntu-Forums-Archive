---
title: "SiS 305 32 MB (PCI) vga troubles"
date: 2008-04-16
forum: General Help
---

### Post by knight666 on 2008-04-16
Hey, 

I love Ubuntu, I really do, but I have a bit of a problem. :(
I recently upgraded my desktop, I bought a new motherboard (Asus K9N-SLI), a new processor (AMD Athlon 2.2 GHz dual-core) and some new RAM (1 GB, eh, maker not important).
But my old video card doesn't fit on my new motherboard, so I'm using a **32 MB SiS 305 PCI card**, which is where trouble comes in.

You see, Ubuntu recognizes the card just fine, it's just that it doesn't give 3D support!
I'm not expecting to run Compiz here, but a splash of slick window-goodness would be nice.

I've tried searching for drivers, but I'm a total noob, I have no idea what I'm doing. :(

Please help.

---

### Post by knight666 on 2008-04-18
It's been several days. :(

---

### Post by kashifsmalik on 2008-04-19
I have been getting the same problem with my much newer nVidia GeForce 7800 GT. However, I have boiled the problem down to "kernel mode glx driver". In my case there's a compatibility issue between the glx driver release by nVidia and the kernel mode glx driver that is built into Ubuntu. Try looking around for "glx driver for SiS 305" and it may help.

---

### Post by pietjanjaap on 2008-04-19
[http://www.winischhofer.eu/linuxsisvga.shtml](http://www.winischhofer.eu/linuxsisvga.shtml)
[http://cs.haifa.ac.il/~skiselev/](http://cs.haifa.ac.il/~skiselev/)
[http://ubuntuforums.org/showthread.php?t=262331&highlight=SiS+305](http://ubuntuforums.org/showthread.php?t=262331&highlight=SiS+305)

---

### Post by knight666 on 2008-04-19
Well when I download it from [http://www.winischhofer.eu/linuxsispart4.shtml#download](http://www.winischhofer.eu/linuxsispart4.shtml#download), it gives me a .o file, while the driver in /usr/lib/xorg/modules/drivers is "sis_drv.so". :\
When I replaced it anyway, Ubuntu got stuck in 800x600 (no fancy effects either) and I had to reload X.org.

Also I have a SiS 305, not a SiS 630.

---

### Post by ryanhaigh on 2008-04-19
I doubt that you will just be able to download any old module/driver file (the .o file) because the driver must be compiled against the kernel you are running, so unless the person who compiled that one was using your version of ubuntu with the same kernel it will not work.

Perhaps you should look through the ubuntuforum post it may be more helpful.

EDIT: just had a look at the thread myself, here is a summary:

OP cant run 3D apps with decent framerate
OP does A LOT of messing around to enable 3D
Someone points out that OP had 3D accel from the start
Complaints about performance and how hard drivers are on linux
Someone recommends getting a nvidia card
No solution offered

---

### Post by knight666 on 2008-04-21
Yeah, that was a great thread.

Could you perhaps guide me through compiling a driver myself?
I'm updating from 7.10 to 8.04 right now, I'll see if it has better drivers for my card.

(sudo update-manager --devel-release, this blog was very helpfu: [http://www.ubuntu-unleashed.com/2008/04/easily-upgrade-to-ubuntu-hardy-heron.html](http://www.ubuntu-unleashed.com/2008/04/easily-upgrade-to-ubuntu-hardy-heron.html))

---

### Post by danwood76 on 2008-04-21
That graphics card is very old and only has 32MB of Vram which will not support much 3D anyway. 
Just get a cheap entry level PCI-E card which will give you what you want plus compiz and so on.

I bought one for my brother the other day for £20 and it plays oblivion and so on in windows.
Im sure it will do a lot in ubuntu aswell.

At the end of the day if you want to run old hardware you have to negate 3D accel and so on.

---

### Post by knight666 on 2008-04-22
Okay, I checked some stuff out, and here's something weird:
It should work!
xorg.conf has DRI enabled for the device section, but it doesn't work.

And running "glxinfo | grep rendering" gives:
Xlib: extension "GLX" missing on display ":0.0".
A bunch of times and an error:
"Error: couldn't find RGB GLX visual"

Help? :(

---

### Post by danwood76 on 2008-04-23
Just because you have DRI enabled in the xorg.conf doesnt mean the driver supports direct rendering.
Your card is old and doesnt have a lot of vram, also its running on the old slow PCI bus, just invest in a new card.

---

### Post by ryanhaigh on 2008-04-23
I know the nvidia driver has issues with glx and composite, its a long shot but you could try adding this to xorg.conf
```

Section "Extensions"
        Option "Composite" "Disable"
EndSection

```

---

