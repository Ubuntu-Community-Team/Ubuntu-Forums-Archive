---
title: "Hybrid Graphics"
date: 2012-12-20
forum: General Help
---

### Post by MourningsEnd on 2012-12-20
So I have a laptop that uses Intel HD Graphics 3000 and GeForce GT 525M with Optimus.

How can I choose what program uses what graphics?  I have not installed a driver from Nvidia yet, and there is nothing in Additional Drivers.

---

### Post by MourningsEnd on 2012-12-21
Bump

---

### Post by seenthelite on 2012-12-21
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by Mark Phelps on 2012-12-21
> **MourningsEnd said:**
> So I have a laptop that uses Intel HD Graphics 3000 and GeForce GT 525M with Optimus.

How can I choose what program uses what graphics?  

You can't -- direct a particular app to use a specific adapter.

---

### Post by sandyd on 2012-12-21
> **Mark Phelps said:**
> You can't -- direct a particular app to use a specific adapter.

You can if you install bumblebee.

Apps that you want to run with the nvidia card, just place "optirun" in front, like
```

optirun firefox
```

---

### Post by seenthelite on 2012-12-21
```
optirun nvidia-settings -c :8
```

Intel HD Graphics 3000 and GeForce GT 525M with Optimus

---

### Post by MourningsEnd on 2012-12-22
> **seenthelite said:**
> [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)


I remember using Bumblebee or some other one that does the same thing.  When I rebooted it made my screen 640x480.

---

### Post by grahammechanical on 2012-12-22
Nvidia does not yet offer a Linux driver with Optimus support.

> A new version of Nvidia's proprietary graphics driver for Linux, in other words, will add Optimus support, making it possible for Linux users to enjoy its battery-saving ability to switch the GPU's power on and off as needed.

[http://www.pcworld.com/article/261874/coming_soon_to_linux_nvidia_optimus_graphics_support.html]("http://www.pcworld.com/article/261874/coming_soon_to_linux_nvidia_optimus_graphics_support.html")

Nvidia are part of the problem. They have yet to become part of the solution.

Regards.

---

### Post by MourningsEnd on 2012-12-22
Okay.  I just added Bumblebee, so how do I remove it?  :oops:

I installed the driver form the Nvidia site, but it does not work or something.  It seem to have disappeared once I installed Bumblebee

---

### Post by seenthelite on 2012-12-22
> **MourningsEnd said:**
> I installed the driver form the Nvidia site
  Why ?  If you want to use Bumblebee  follow the instructions on the wiki I posted the link for.
You may have to purge the driver you installed  and then install Bumblebee, it does work, as the screenshot I posted shows.

[http://en.wikipedia.org/wiki/Nvidia_Optimus](http://en.wikipedia.org/wiki/Nvidia_Optimus)

> Okay.  I just added Bumblebee, so how do I remove it?

To remove

If you're unsatisfied with Bumblebee, you can remove it via: 
[LIST=1]
[*]sudo apt-get install ppa-purge 
[*]sudo ppa-purge ppa:bumblebee/stable 
[/LIST]
If  you want to keep some programs from the bumblebee repository, you can  also suffice by removing Bumblebee only (including its dependencies): 

[LIST=1]
[*]sudo apt-get purge bumblebee 
[*]sudo apt-get --purge autoremove
[/LIST]
(From the same wiki page)

---

### Post by seenthelite on 2012-12-22
> How can I choose what program uses what graphics?

After installing Bumblebee,

```
glxspheres
Polygons in scene: 62464
Visual ID of window: 0x9f
Context is Direct
OpenGL Renderer: Mesa DRI Intel(R) Sandybridge Mobile 
59.872883 frames/sec - 52.415117 Mpixels/sec
```

```
optirun glxspheres
Polygons in scene: 62464
Visual ID of window: 0x21
Context is Direct
OpenGL Renderer: GeForce GT 525M/PCIe/SSE2
129.903663 frames/sec - 113.722863 Mpixels/sec
```

---

