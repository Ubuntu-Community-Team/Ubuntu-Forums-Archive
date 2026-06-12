---
title: "Really slow X, broken glx... this is a show-stopper!"
date: 2005-10-17
forum: General Help
---

### Post by RustyFox on 2005-10-17
I've been really puzzled by this release of Ubtuntu so far. Most other peoples experiences have nothing but praise, yet I've installed it on two different machines (which both previously ran sarge) and found this to be the slowest performing distro I've ever used - despite it using the 'faster' Xorg.

Firstly, on my Athlon Thunderbird (using -386, -686 and -k7 kernels) glxinfo / glxgears reports:

name of display: :0.0
Illegal instruction

Nothing 3D appears to work, I'm using a Radeon 9200SE AGP card. That's bad enough, but meanwhile, on this machine and the Duron / Matrox G400 desktop graphics performance is abysmal. As an example, moving windows around, there's shadows everywhere, and it might take almost a second to fully redraw the screen once I've dropped a window. Same with minimising. Xorg "feels" much much slower than Xfree86 did on sarge on both machines, to the point that using this cutting edge distro is a nightmare! The sort of performance I'd expect from XP with a VGA driver. While glx seems to work on the duron/mga machine, it's also much much slower than it was with Sarge. I would have expected this to be the other way round. Oh, and glxgears doesn't report any framerate anymore. (Yeah, I know it's no benchmark, but still an indication of whether something's working or not!)

Am I missing something profound? Other than these issues, Breezy is otherwise perfection, but this slowness / refusal for 3D to work on my machine is a real show stopper!

---

### Post by RustyFox on 2005-10-17
To partly answer my own question, installing the xorg-driver-fglrx seems to have got 3D working, but the 3D screensavers as an example as MUCH slower than under sarge, so something can't be right somewhere.

2D performance is just as dire too.

---

### Post by Qrk on 2005-10-17
You need to enable 3-D by installing the nvidia-glx package. Follow the instructions in
 
System-->help-->starterguide-->hardware

It speeds everything up considerably.

---

### Post by RustyFox on 2005-10-17
Umm, nvidia-glx is for nvidia cards, unless something profounds changed here.

I'm using ATI (Radeon 9200SE) and Matrox (G400) cards, and while DRI is working on each, both 2D and 3D is seriously slow to the point of being obviously wrong.

---

### Post by RustyFox on 2005-10-17
Again to partly answer my own question, I found the package with the closed source kernel modules, so the fglrx kernel module is loaded now - and my radeon 9200SE machine is running much better! 3D is impressive, and while 2D has sped up, it isn't quite as nippy as I feel it ought to be.

This still leaves the Matrox machine performing much too slow. There's no kernel modules I can see for matrox cards, and 2D/3D are both painfully slow compared to Xfree86 in Sarge, so I still get the impression something, somewhere isn't playing nicely.x

---

### Post by lithorus on 2005-10-17
2D on ATI is horribly slow since things like RENDER is not accelrated and I have a feeling accelrated RENDER is getting much more important now we have cairo. I recently tested my ATI and the first thing I noticed was the horrible slowness of X compared to my nvidia. I would guess that it's even worse with the matrox card.

---

### Post by RustyFox on 2005-10-17
Well, the matrox cards have performed extremely well under any other XFree86 based distro for years before Ubuntu, so I find it hard to swallow that the mga drivers would have taken a step back with Xorg. I used to swear by matrox simply because the Xfree86 drivers were so damn good for desktop use.

Something's up, but I don't know what.

---

