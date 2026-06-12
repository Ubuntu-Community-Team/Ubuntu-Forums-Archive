---
title: "How to install this? (Is it even possible?)"
date: 2007-02-24
forum: General Help
---

### Post by Sitix on 2007-02-24
Hey,

I was trying to get a driver for my SiS graphical card. (I have a laptop, so I can't just put a better supported one in..) I looked on the SiS website and found the driver called 'sis_drv.o-410'. But I can't find a way to install it. The file is originally meant for Redhat 7.2.

Sadly, there are no sources or deb/rpm packages available for it. So I'm kind of wondering how to do this. :P

Thanks in advance!

PS: It is the SiS650 & SiS740 series, you can get it at [www.sis.com](www.sis.com) --> download --> explains itself, I suppose...

---

### Post by az on 2007-02-24
> **Sitix said:**
> Hey,

I was trying to get a driver for my SiS graphical card. (I have a laptop, so I can't just put a better supported one in..) I looked on the SiS website and found the driver called 'sis_drv.o-410'. But I can't find a way to install it. The file is originally meant for Redhat 7.2.

Sadly, there are no sources or deb/rpm packages available for it. So I'm kind of wondering how to do this. :P

Thanks in advance!

PS: It is the SiS650 & SiS740 series, you can get it at [www.sis.com](www.sis.com) --> download --> explains itself, I suppose...

There are a few SIS chipsets that do not offer 3d hardware acceleration.  If your card is supported, the driver is already part of the xorg package, which you already have installed.

What exactly is the problem?

---

### Post by Sitix on 2007-02-25
Well, the problem is that I want to try to install Compiz. Or, rather, I want to get it to work. Before installing, I was suggested to check if I had 3D hardware acceleration supported on my chipset with glxinfo. But no results, and so I thought the problem had to be the driver. Because it didn't know what to do with my whole chipset at all and I don't think there is a proper driver for it already in the Ubuntu base package.

It doesn't do anything in Compiz, for example, except taking away my Metacity bars and things without putting anything in place.

It's not a disaster if it doesn't work, but I'd really like it to.

---

### Post by az on 2007-02-25
I doubt Sis provides enough hardware acceleration to run Compiz.

---

