---
title: "AMD / Radeon: Some big pictures become pink"
date: 2012-11-29
forum: General Help
---

### Post by Broobie on 2012-11-29
This is very odd. I have Ubuntu 12.04 64 bits and all work fine and graphical of my applications and Unity watch fine too, but often when I open a big image (2.272px × 1.521px) is pink!

For example, I see this picture and all is normal its color is like normal parquet: [http://www.sxc.hu/photo/1163639](http://www.sxc.hu/photo/1163639)

but when I open it, image becomes color pink: [http://www.sxc.hu/pic/l/h/hi/hisks/1163639_31172501.jpg](http://www.sxc.hu/pic/l/h/hi/hisks/1163639_31172501.jpg)


If I do ```
fglrxinfo
``` all is like always:
```

display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: ATI Radeon HD 5800 Series 
OpenGL version string: 4.2.11762 Compatibility Profile Context
```Any idea why occur this? :confused:

---

### Post by sdowney717 on 2012-11-29
this is how it looks using Nvidia proprietary binary driver.
What driver are you using?

---

### Post by sdowney717 on 2012-11-29
right click save the file
[http://www.sxc.hu/pic/l/h/hi/hisks/1163639_31172501.jpg](http://www.sxc.hu/pic/l/h/hi/hisks/1163639_31172501.jpg)
then click on it in file manager and see what it looks like.

---

### Post by Broobie on 2012-11-30
I have AMD drivers: ```
sudo lshw -c video
```

```
  *-display               
       descripción: VGA compatible controller
       producto: Cypress [Radeon HD 5800 Series]
       fabricante: Hynix Semiconductor (Hyundai Electronics)
       id físico: 0
       información del bus: pci@0000:03:00.0
       versión: 00
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm pciexpress msi vga_controller bus_master cap_list rom
       configuración: driver=fglrx_pci latency=0
       recursos: irq:58 memoria:e0000000-efffffff memoria:fb5c0000-fb5dffff ioport:be00(size=256) memoria:fb500000-fb51ffff
```

And ```
modinfo fglrx
```
```

filename:       /lib/modules/3.2.0-33-generic/updates/dkms/fglrx.ko
license:        Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY
description:    ATI Fire GL
author:         Fire GL - ATI Research GmbH, Germany
srcversion:     C6C0E9E86E927C954E5BD73
alias:          pci:v00001002d000068F2sv*sd*bc*sc*i*
//many alias later...
alias:          pci:v00001002d00009830sv*sd*bc*sc*i*
depends:        
vermagic:       3.2.0-33-generic SMP mod_unload modversions 
parm:           firegl:charp
```

And ```
jockey-text -l
```

```
xorg:fglrx - Graphics proprietary module FGLRX for ATI/AMD (Privative, Activated, In Use)
xorg:fglrx_updates - Graphics module FGLRX proprietary of ATI/AMD (updates post-lanzamiento) (Privative, Off, Not in Use)

```

Your first image I see it perfect, but the second I see it pink again.

---

### Post by Broobie on 2012-11-30
This is more odd yet. I just opened [http://www.sxc.hu/pic/l/h/hi/hisks/1163639_31172501.jpg](http://www.sxc.hu/pic/l/h/hi/hisks/1163639_31172501.jpg) with Opera and all works fine. So I thought it was a bug of firefox only. Surprise, when I save with Opera the image on my hard disk all pink again. :mad:

In short:

With Opera I can load the image on browser and I see it fine.
With Firefox I see a pink image.

When I save in my disk with both, next when I open is pink again.

---

### Post by Wim Sturkenboom on 2012-11-30
Not of help, only information

[http://www.sxc.hu/pic/l/h/hi/hisks/1163639_31172501.jpg](http://www.sxc.hu/pic/l/h/hi/hisks/1163639_31172501.jpg) looks fine in firefox; downloaded it as well and looks fine in eye-of-gnome

I'm using intel graphics (integrated in i3)

---

### Post by Broobie on 2012-11-30
Thank you Wim. I guess it. Like I see the image is: [[IMG]http://imageshack.us/a/img826/7857/capturepink.th.png[/IMG]](http://imageshack.us/photo/my-images/826/capturepink.png/)

I changed my Proprietary ATI drivers to Open Source and happens same behaviour. In fact, this happen with other images with similar tone (for example images about timber or parquet)

---

### Post by sdowney717 on 2012-11-30
why not try creating a live usb. Try a different version of ubuntu like 12.04 versus 12.10

boot from the usb and look at the colors.
if normal then problem is your current config.

---

### Post by Broobie on 2012-12-01
I tested it from 12.10 version and all works fine. Then it has to be something about my config. But I don't know where look it, because on cccamd all seems fine with colors.

How can I move the config / module / driver of the live usb to my installed ubuntu? Do you know what folders I need? Because I don't enough know about modules in linux.

---

