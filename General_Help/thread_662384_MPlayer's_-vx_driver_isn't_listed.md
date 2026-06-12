---
title: "MPlayer's -vx driver isn't listed"
date: 2008-01-08
forum: General Help
---

### Post by ~LoKe on 2008-01-08
**EDIT**: Compiling with --enable-xv, something I failed to look for previously.  I'll mark as solved if the solution is so simple.
Just as the title suggests.

>  mplayer -vo help
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz (Family: 6, Model: 15, Stepping: 11)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
Available video output drivers:
        x11     X11 ( XImage/Shm )
        xover   General X11 driver for overlay capable video output drivers
        gl      X11 (OpenGL)
        gl2     X11 (OpenGL) - multiple textures version
        fbdev   Framebuffer Device
        fbdev2  Framebuffer Device
        v4l2    V4L2 MPEG Video Decoder Output
        xvidix  X11 (VIDIX)
        cvidix  console VIDIX
        null    Null video output
        mpegpes Mpeg-PES to DVB card
        yuv4mpeg        yuv4mpeg output for mjpegtools
        png     PNG file
        jpeg    JPEG file
        tga     Targa output
        pnm     PPM/PGM/PGMYUV file
        md5sum  md5sum of each frame

Is it something I have to enable while compiling?  If so, how?  --enable-vc?

---

