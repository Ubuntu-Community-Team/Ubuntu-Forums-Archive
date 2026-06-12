---
title: "NVIDIA GeForce4 MX 440 - Lubuntu"
date: 2014-01-09
forum: General Help
---

### Post by scullboy491 on 2014-01-09
Could someone please help me, I have the log in the link below. I'm trying to install 331.20 NVIDIA Linux graphics driver, but i keep getting this error nvidia.ko

[http://pastebin.com/ymn60EA3](http://pastebin.com/ymn60EA3)

---

### Post by Yellow Pasque on 2014-01-09
It's not going to work...
> WARNING: The NVIDIA GeForce4 MX 440 with AGP8X GPU installed in this system is supported through the **NVIDIA 96.43.xx legacy** Linux graphics drivers.  Please visit [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) for more information.  The 331.20 NVIDIA Linux graphics driver will ignore this GPU.

I don't even think the nvidia 96.xx driver will run in anything newer than Precise. You're limited to nouveau open source driver on any newer version of Ubuntu.

---

