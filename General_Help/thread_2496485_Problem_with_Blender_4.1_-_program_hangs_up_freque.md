---
title: "Problem with Blender 4.1 - program hangs up frequently"
date: 2024-03-30
forum: General Help
---

### Post by thezacho on 2024-03-30
Hy,

I run Ubuntu 20.04.6 LTS on a PC an with Intel® Core™ i5-7400 CPU @ 3.00GHz × 4  and a Mesa Intel® HD Graphics 630 (KBL GT2) / AMD® Redwood.

Many times when I use Blender, the program suddenly hangs up and I can't do anything anymore. When I launch the System Monitor I see, that one of the four processor cores runs at 100%, all the other three are running low. I can't do anything but stall the application and start it again. 

It doesn't really depend on how big the Blender file is, it happens quite randomly, as I see it.

Can anybody help, what the problem could be?

Thanks in advance.

Cheers Michael

---

### Post by thegribble on 2024-04-01
I'm having the same problem - hangs almost immediately with one core at 100% when I load a scene, never recovers. i3-8130U CPU x 4 and Intel UHD  graphics 620 so maybe a graphics driver issue? 
I have dual boot on here and can confirm that blender 4.1 works fine under Windows on the same laptop without the same issue.

---

### Post by cyrgui on 2024-04-01
Same for me, [COLOR=#000000]hangs almost immediately on my laptop Lenovo [/COLOR]Intel(R) Core(TM) i5-6200U CPU @ 2.30GHz Ubuntu 22.04.4 LTS with 16 Go Ram. [COLOR=#000000]Blender 3.x was working fine.[/COLOR]

---

### Post by thegribble on 2024-04-05
Found the answer, I think, courtesy of this post: [https://askubuntu.com/questions/1477715/blender-hangs-using-intel-integrated-graphics/1482720#1482720?newreg=bba0adf61fc740f08755b9748f66e1c0](https://askubuntu.com/questions/1477715/blender-hangs-using-intel-integrated-graphics/1482720#1482720?newreg=bba0adf61fc740f08755b9748f66e1c0)

First you change a driver parameter, then run blender with an environment variable set. needs to be done every boot so I put these two commands in a shell script:

$ echo 10000 | sudo tee /sys/class/drm/card0/engine/rcs0/preempt_timeout_ms
$ INTEL_DEBUG=reemit blender

---

### Post by cyrgui on 2024-04-28
Thank's ! It works great, I hope dev will incorpore this in a release...

---

### Post by bitbyter2k on 2024-11-18
echo 10000 | sudo tee /sys/devices/pci0000:00/0000:00:02.0/drm/card1/engine/rcs0/preempt_timeout_ms

did the trick for me on Ubuntu 24.04 with Nvidia card and Blender 4.02 and 4.2.3
stable now, no more freezing

---

