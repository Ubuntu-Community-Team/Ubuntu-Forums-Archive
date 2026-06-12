---
title: "Slow graphics Intel GMA 3650"
date: 2013-03-17
forum: General Help
---

### Post by fabiomassudo on 2013-03-17
Hi,

I have a Intel GMA 3650. My videos are very very slow. I cant find any drivers. Can yiu help me?

Ty.

---

### Post by sanderj on 2013-03-17
> **fabiomassudo said:**
> Hi,

I have a Intel GMA 3650. My videos are very very slow. I cant find any drivers. Can yiu help me?

Ty.

See [http://en.wikipedia.org/wiki/Intel_GMA#PowerVR_based](http://en.wikipedia.org/wiki/Intel_GMA#PowerVR_based) and [https://wiki.archlinux.org/index.php/Poulsbo](https://wiki.archlinux.org/index.php/Poulsbo)

So: bad support on Linux. You could try the driver suggestions on the second link.

HTH

---

### Post by fabiomassudo on 2013-03-17
Im new here, can you explain me, how to install that driver?

---

### Post by sanderj on 2013-03-17
> **fabiomassudo said:**
> Im new here, can you explain me, how to install that driver?

Maybe it's already installed. Open a terminal and do this:

```
lsmod | grep -i gma
```

Post the output here.

If there is no output, read [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

---

### Post by fabiomassudo on 2013-03-17
Thank you for your help

---

### Post by sanderj on 2013-03-17
So the gma500_gfx driver is already in use. That's good news. The bad news: you won't get better experience.

You have the Toshiba NB510 netbook? When I bought my netbook, I selected it on **not** having the GMA500 hardware, because of its bad Linux support.

EDIT:

Maybe [https://wiki.archlinux.org/index.php/Poulsbo#Poor_video_performance](https://wiki.archlinux.org/index.php/Poulsbo#Poor_video_performance) provides some help ...

---

### Post by fabiomassudo on 2013-03-17
Yes, i have the NB510. Help me with those command lines please.

---

### Post by sanderj on 2013-03-17
> **fabiomassudo said:**
> Help me with those command lines please.

Sorry, I can't; I haven't got a GMA 500. The instructions need hands-on trial-and-error.

---

### Post by diebels on 2013-04-28
With cedarview drivers from 12.04 updates repository the Intel gma3650 / PowerVR SGX545 can do 1080p video allright with VLC and mplayer vaapi.  Intel has made up an old version of chromium (13) that give you accelerated flash but it's a bit of an ordeal to get hold of.  Gnome classic is usable but a bit sluggish at 1920x1080 resolution. There's no full OpenGL support, but some OpenGL ES which isn't too useful on the ubuntu desktop yet, so forget about most 3d games or UI's.

---

### Post by gordintoronto on 2013-04-28
You also should keep in mind that the CPU is extremely slow, and some video players depend entirely on the CPU.

---

### Post by texadactyl on 2013-09-06
I have an Intel D2550MUD2 motherboard (NM10 chipset and GMA3650).  In Xubuntu saucy (13.10), kernel module gma500_gfx and the modesetting X driver were autoselected for my installation.  This works fairly well for a programmer (me) although it might be sub-optimal for an Ubuntu Studio user.  At least, I can use the full display resolution capability (1920x1080x60) of my 22" monitor.

I would stay away from using custom graphics drivers if possible.

---

