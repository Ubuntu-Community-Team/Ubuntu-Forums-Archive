---
title: "Hardy sluggish compared to Gutsy... why?"
date: 2008-06-06
forum: General Help
---

### Post by ocularb0b on 2008-06-06
So i've done a clean install of Hardy on my machine and it is much slower than Gutsy was on the same hardware.  I cant even play a DVD without dropping tons of frames.  Compiz runs at about half the framerate.  I'm not sure what to do here.  It seems to affect pretty much everything even shell operations outside of X.  This leads me to think its at the kernel level.  In Gutsy my system stayed snappy even while doing blender renders with both cores.  Has the default sheduler changed? Can we expect this to improve or will i have to find another distro?

---

### Post by sonofusion82 on 2008-06-06
hardy is working fine for me.

if you are doing a clean install, it could be probably wrong hardware/driver settings detected.  harddisk DMA, x configuration, or others?

---

### Post by ocularb0b on 2008-06-06
hdparm shows my drive using UDMA5, and i moved my xorg.conf from my gutsy system, im looking for other culprits....
and no trackerd is not running :) , i know where things are on my system so i never use indexing.

---

### Post by hyper_ch on 2008-06-06
open a terminal and run:
```

glxgears

```

How many fps do you get?

---

### Post by ukripper on 2008-06-06
Have you installed all updates yet?

---

### Post by ocularb0b on 2008-06-06
glxgears runs about 100fps.  All packages are up to date.
I have almost 3gb of free ram (not swap).  And cpu is not being eaten up by anything.
Generally things are working ok, just with unusual latency

---

### Post by ocularb0b on 2008-06-06
it seems that the default kernel is configured with CONFIG_HZ_250 which seems like a better setting for a server than a desktop, but i think that was the case for gutsy as well.  I think im going to roll my own just for the fun of it.

---

### Post by ukripper on 2008-06-06
> **ocularb0b said:**
> it seems that the default kernel is configured with CONFIG_HZ_250 which seems like a better setting for a server than a desktop, but i think that was the case for gutsy as well.  I think im going to roll my own just for the fun of it.

Are you using ATI graphics card?

---

### Post by ocularb0b on 2008-06-06
nvidia gforce7150m,  which is one of the shared memory jobs.
interestingly i ran glxgears in a fluxbox session without compiz and got almost 1000fps
vs. 100fps in gnome with compiz
not a subtle difference.

---

### Post by hyper_ch on 2008-06-06
yeah, the fps seem really low....

when in gnome, install htop
```

sudo apt-get install htop

```
and run it
```

htop

```

and then check use your compute like normal and check when it's sluggy what uses all this cpu...

---

### Post by ocularb0b on 2008-06-06
strange,  after starting a new gnome session things are zippy like they ought to be, and glxgears runs around 800fps.  My experience in the last year or so is that even when the CPU is getting hammered normal stuff like opening windows and audio/video playback are still very responsive.  And now while running glxgears twice to load both cores, things are still good.  
after starting a new session, but 30 mins or so after logging in, it wanks out again. i see nothing new in htop and cpu usage in below 20%.

---

### Post by danwood76 on 2008-06-06
What version of the nvidia drivers are you using?
Sounds like a memory leak to me.

---

### Post by ocularb0b on 2008-06-06
nvidia driver version 169.12

---

### Post by ocularb0b on 2008-06-06
yeah dan i think you were right, or at least that it is a problem with the nvidia driver.  I built my own kernel (latest stable from kernel.org) and intalled the driver with package from nvidia.com.  Things seem fine now.  I expect this will get worked out with the next driver ver. in ubuntu.
Thanks all for your help.

---

### Post by raozuzu on 2008-06-10
Have you tried also adding
Option "UseEvents" "True"
in the "device" section of your xorg.conf... that solution solved many problems to other users ;)

---

### Post by jwalker on 2008-06-17
Hi

If anybody has found their way here and wants further confirmation, the suggestion about the nvidia drivers is correct, at least in my case. I went from what ubuntu's 'Hardware Drivers' installed (69.something.something) to 173.14.09 and my performance has increased considerably. So I'm a happy man. 

Good luck, thanks to whoever suggested the driver update.

---

