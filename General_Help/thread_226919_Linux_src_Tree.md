---
title: "Linux src Tree"
date: 2006-07-31
forum: General Help
---

### Post by rold50 on 2006-07-31
Hi All,

I'm trying to install a driver for my pcmcia card.
In the installation instructions it had:
   
   4) In the Linux src tree, add
       a) obj-$(CONFIG_PCMCIA_IMPERX_VCE) += imperxvce_cs.o  to
          linux/drivers/media/video/Makefile
       b) dep_tristate '  Imperx Video Capture Essentials PCMCIA support'
          CONFIG_PCMCIA_IMPERX_VCE $CONFIG_VIDEO_DEV $CONFIG_PCMCIA to
          linux/drivers/media/video/Config.in
       c) When building the kernel, make sure to set the driver as a module
          in the configuration.

    5) Build the kernel the usual way and modules too.

where do I find the linux/drivers/ folder? I can't seem to find it? Do I have to install some linux package?

Also How do I build the kernel/modules? I never built the kernel I just updated using adept/package manager

Thanks :D

---

### Post by rold50 on 2006-08-01
bump?

please help :(

---

### Post by RAOF on 2006-08-01
You're probably after this howto: [http://www.ubuntuforums.org/showthread.php?t=85064&highlight=kernel+build](http://www.ubuntuforums.org/showthread.php?t=85064&highlight=kernel+build)

---

