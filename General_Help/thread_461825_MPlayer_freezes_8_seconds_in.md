---
title: "MPlayer freezes 8 seconds in"
date: 2007-06-02
forum: General Help
---

### Post by mmilitia9 on 2007-06-02
lol.. I've come far tonight. I've managed to get everything playing in one media player(GMplayer) and everything works fine.  Although, Apple Trailers gives me some crap.  It freezes a few seconds into the video.

Any suggestions?

Thanks,

Dominick

(Any specific settings?  I havent touched any preferences yet in Mplayer.. I give up for the night.. It's almost 4AM!... Linux keeps u active :) )

---

### Post by jjacobs2 on 2007-06-02
Open a terminal, navigate to the directory with the videos, type "gmplayer videoname.mov"  without the quotes and hit enter.  You can type the first few letters of the video name and hit tab to finish it.  Copy and paste the text that mplayer prints in the terminal on here.

---

### Post by mmilitia9 on 2007-06-02
Well, I'm not DLing movie.. I'm just streaming.

---

### Post by mmilitia9 on 2007-06-02
But I downloaded a sample mov from a website to give you this...Hope u can do something with it..

dominick@dominick-desktop:~$ cd /home/dominick/Documents
dominick@dominick-desktop:~/Documents$ gmplayer city_lights.mov
MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.80GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/dominick/Documents/city_lights.mov.
Quicktime/MOV file format detected.
VIDEO:  [mjpa]  320x240  24bpp  15.000 fps    0.0 kbps ( 0.0 kbyte/s)
[gl] using extended formats. Use -vo gl:nomanyfmts if playback fails.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffmjpeg] vfm: ffmpeg (FFmpeg MJPEG decoder)
==========================================================================
Audio: no sound
Starting playback...
VDec: vo config request - 320 x 240 (preferred colorspace: Planar 422P)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar 422P as output csp (no 1)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
SwScaler: using unscaled yuv422p -> rgb32 special converter
VO: [gl] 320x240 => 320x240 BGRA 
V:   8.0 121/121  5%  3%  0.0% 0 0

---

