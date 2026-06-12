---
title: "live cd allows 1024x768. Installed stuck at 640x480. Core i5 3550"
date: 2017-07-08
forum: General Help
---

### Post by link626 on 2017-07-08
Trying to successfully install ubuntu on a core i5 3550 dedicated server.

within Live CD, I can view resolution at 1024x768. The installed 16.04 has only max res 640 480.

I have nomodeset in the grub.

How do I get the resolution higher?

why does the live CD allow higher resolution, when both are running nomodeset ?


This cpu has HD4000 graphics, and as I understand, 16.04 has graphics support for this gpu.


please help me troubleshoot. Where to look.

xrandr says my only graphics mode is 640 480

---

### Post by link626 on 2017-07-09
I managed to semi fix by editing /etc/default/grub with these 2 lines

GRUB_GFXMODE= #x#x#
GRUB_GFXPAYLOAD_LINUX=keep

It forces the resolution.

vbeinfo says this gpu supports 1920x1080

dunno why the OS locks me into 640x480 otherwise.

---

