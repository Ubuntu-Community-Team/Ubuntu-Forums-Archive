---
title: "Ubuntu 18.04 + intel i7-9700K + Intel UHD Graphics 630 = no HW acceleration - why?"
date: 2019-03-03
forum: General Help
---

### Post by bullwinkle2 on 2019-03-03
I tried installing Ubuntu 18.04 today on a system with Intel UHD Graphics 630 (Intel i7-9700K CPU) and could not get any form or hardware acceleration to work.  When I installed and ran vainfo, I got this:

libva info: VA-API version 1.1.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: Found init function __vaDriverInit_1_1
libva error: /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so init failed
libva info: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit

The i965_drv_video.so file does exist, and I tried a bunch of things including upgrading the BIOS (Gigabyte Z390 I AORUS PRO WIFI board) to the latest, all without success.  Any ideas as to what I have to do to get rid of this error so hardware acceleration will work?

---

