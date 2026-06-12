---
title: "mplayer -vo not working"
date: 2006-12-22
forum: General Help
---

### Post by isw on 2006-12-22
Hello,

I compiled and installed MPlayer-1.0rc1 with ./configure make and make install.

It compiled without problems, but non of the videooutput (-vo) works.
These are the options by mplayer -vo help
 Available video output drivers:
        fbdev   Framebuffer Device
        fbdev2  Framebuffer Device
        cvidix  console VIDIX
        null    Null video output
        mpegpes Mpeg-PES to DVB card
        yuv4mpeg        yuv4mpeg output for mjpegtools
        png     PNG file
        tga     Targa output
        pnm     PPM/PGM/PGMYUV file
        md5sum  md5sum of each frame


The previous version used x11 or xv as videooutput.

Sounds works fine (alsa).

Any suggestions to get more drivers?

:-k

---

### Post by isw on 2006-12-22
ok... got it working, installed develop packages for x11 :)

---

