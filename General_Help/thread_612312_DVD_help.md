---
title: "DVD help"
date: 2007-11-13
forum: General Help
---

### Post by darkblade25 on 2007-11-13
I have several encrypted dvd and I followed this [https://help.ubuntu.com/7.04/musicvideophotos/C/video.html#video-dvd](https://help.ubuntu.com/7.04/musicvideophotos/C/video.html#video-dvd) tutorial. Now, I have Mplayer playing dvds but not totem movie player. Does anyone know why?

I dont know if this helps, but when I tried to install Kaffiene, it says that my dvd drive: Cant not check DMA mode.

---

### Post by darkblade25 on 2007-11-13
Finally figured it out, if anyone is have the same problem, my solution was my dvd drive did not have dma turned on, so I have to on to /etc/hdparm.conf and turn it on there. 
I works after restarted. :)

---

