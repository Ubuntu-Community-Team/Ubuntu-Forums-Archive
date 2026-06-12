---
title: "mplayer cant play video"
date: 2006-11-16
forum: General Help
---

### Post by pontifex3 on 2006-11-16
hi, i had some .rm files i couldnt play with mplayer so i uninstalled it from synaptic and compiled it from source adding the codecs but now mplayer cant play any video type it just plays the audio, if i run it as a normal user i get 

```
...
Can't open /dev/fb0: Permission denied
[fbdev2] Can't open /dev/fb0: Permission denied
vo_cvidix: No vidix driver name provided, probing available ones (-v option for details)!
[VO_SUB_VIDIX] Couldn't find working VIDIX driver.
==========================================================================
Opening video decoder: [realvid] RealVideo decoder
Selected video codec: [rv3040] vfm: realvid (Linux RealPlayer 10 RV30/40 decoder)
==========================================================================
...

```
and if i use sudo 

```
...
Can't open /dev/fb0: No such device
[fbdev2] Can't open /dev/fb0: No such device
vo_cvidix: No vidix driver name provided, probing available ones (-v option for details)!
[VO_SUB_VIDIX] Couldn't find working VIDIX driver.
==========================================================================
Opening video decoder: [realvid] RealVideo decoder
Selected video codec: [rv3040] vfm: realvid (Linux RealPlayer 10 RV30/40 decode
...
```

i have searched and found absolutely no information on vidix driver and what /dev/fb0 should be, any help appreciated, thanks in advance
here's the full code i get (even though i have an amd64, i have edgy for 32 bits, im not sure if that causes any trouble.. at least i dont think it should):

```
jjara@geburah:~/computadora/Escuela/MIT/Introduction to Algorithms$ sudo mplayer class1.rm 
Password:
MPlayer 1.0rc1-4.1.2 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3200+ (Family: 15, Model: 4, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE SSE2

Playing class1.rm.
REAL file format detected.
Stream description: Video Stream
Stream mimetype: video/x-pn-realvideo
Stream description: Audio Stream
Stream mimetype: audio/x-pn-realaudio
Stream mimetype: logical-fileinfo
VIDEO:  [RV30]  320x240  24bpp  15.000 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 name:  
 author: Academic Media Production Services
 copyright: (c) 2006 Massachusetts Institute of Technology
Can't open /dev/fb0: No such device
[fbdev2] Can't open /dev/fb0: No such device
vo_cvidix: No vidix driver name provided, probing available ones (-v option for details)!
[VO_SUB_VIDIX] Couldn't find working VIDIX driver.
==========================================================================
Opening video decoder: [realvid] RealVideo decoder
Selected video codec: [rv3040] vfm: realvid (Linux RealPlayer 10 RV30/40 decoder)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 22050 Hz, 1 ch, s16le, 32.0 kbit/9.08% (ratio: 4005->44100)
Selected audio codec: [ffcook] afm: ffmpeg (FFmpeg COOK audio decoder)
==========================================================================
AO: [oss] 22050Hz 1ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 320 x 240 (preferred colorspace: Planar I420)
VDec: using Planar I420 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [null] 320x240 => 320x240 Planar I420 
A:  13.1 V:  13.1 A-V:  0.003 ct: -0.130 198/198  2%  0%  0.4% 0 0              
[1]+  Stopped                 sudo mplayer class1.rm
jjara@geburah:~/computadora/Escuela/MIT/Introduction to Algorithms$ 

```

---

### Post by taurus on 2006-11-16
You need to install the codecs before you can play any video.  The easiest way is to install automatix2 and use it to install everything else...

[http://www.getautomatix.com](http://www.getautomatix.com)

---

