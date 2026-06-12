---
title: "graphics drivers"
date: 2013-05-09
forum: General Help
---

### Post by Isaacmarritt on 2013-05-09
hi  noticed that games on my laptop were running very slow i think this is because the drivers for my GPU are not the right drivers or the best for my card so i went on intels website and they sent me to this website [https://01.org/linuxgraphics/downloads](https://01.org/linuxgraphics/downloads)  to look for the drivers for my GPU but i dont know witch driver to download could someone please point me in the right direction . thank you all:KS
also  my GPU is Intel® 965GM x86/MMX/SSE2

---

### Post by Cheesemill on 2013-05-09
The Intel graphics drivers are built in to Ubuntu, you're already using them.

---

### Post by gifford on 2013-05-09
The new intel graphics driver package is not yet available for your version of Ubuntu.
See: [http://www.webupd8.org/2013/04/how-to-use-intel-linux-graphics-drivers.html](http://www.webupd8.org/2013/04/how-to-use-intel-linux-graphics-drivers.html)

---

### Post by Isaacmarritt on 2013-05-09
thanks for the help when do you think it will come out for 13.04

---

### Post by Cheesemill on 2013-05-10
As I said in my earlier post, ***you're already using the latest Intel driver***.

The version in the standard 13.04 repositories is 2.21.6, which is actually a newer version than the 2.21.3 that is available from the Intel site.
[http://packages.ubuntu.com/search?keywords=xserver-xorg-video-intel&searchon=names&exact=1&suite=all&section=all](http://packages.ubuntu.com/search?keywords=xserver-xorg-video-intel&searchon=names&exact=1&suite=all&section=all)

---

### Post by Mark Phelps on 2013-05-10
> **Isaacmarritt said:**
> thanks for the help when do you think it will come out for 13.04

If you're asking when is Intel going to write NEW drivers for that chipset, the answer most likely is -- never.

That is a very old chipset and the drivers that are out there now are all there are going to be.

---

