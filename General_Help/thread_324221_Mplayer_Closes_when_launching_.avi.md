---
title: "Mplayer Closes when launching .avi"
date: 2006-12-23
forum: General Help
---

### Post by WalmartSniperLX on 2006-12-23
Is there a certain plugin that you need inorder to play .avi videos in mplayer? When I launch .avi videos mplayer just shuts down. Maybe theres a setting?

---

### Post by taurus on 2006-12-23
I suppose you already installed the codecs!  What if you run it from a terminal to see exactly what the error message is?

```
gmplayer **filename.avi**
```

---

### Post by WalmartSniperLX on 2006-12-23
> **taurus said:**
> I suppose you already installed the codecs!  What if you run it from a terminal to see exactly what the error message is?

```
gmplayer **filename.avi**
```

Why didnt I think of that before ](*,) 

Well momment I opened it using the terminal it played :D

heres the output:

```
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: AMD Sempron(tm) Processor 3100+ (Family: 15, Model: 44, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.

Playing /home/patrick/Shared/Jackie Chan - Rush Hour 2.avi.
AVI file format detected.
VIDEO:  [DIV3]  576x240  24bpp  23.976 fps  932.5 kbps (113.8 kbyte/s)
Clip info:
 Software: Nandub v1.0rc2
==========================================================================
Requested audio codec family [mp3] (afm=mp3lib) not available.
Enable it at compilation.
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 141.6 kbit/9.22% (ratio: 17696->192000)
Selected audio codec: [ffmp3] afm: ffmpeg (FFmpeg MPEG layer-3 audio decoder)
==========================================================================
open: No such file or directory
Couldn't open: /dev/mga_vid
open: No such file or directory
Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffdivx] vfm: ffmpeg (FFmpeg DivX ;-) (MS MPEG-4 v3))
==========================================================================
alsa-init: using device default
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 576 x 240 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 576x240 => 576x240 Planar YV12 

```

---

### Post by taurus on 2006-12-23
In your ~/.mplayer/gui.conf, make sure these two lines look like the following...

```

v_vfm = "ffmpeg"
a_afm = "ffmpeg"

```

---

### Post by WalmartSniperLX on 2006-12-23
> **taurus said:**
> In your ~/.mplayer/gui.conf, make sure these two lines look like the following...

```

v_vfm = "ffmpeg"
a_afm = "ffmpeg"

```

Thank you very much. Works perfectly :D

---

### Post by taurus on 2006-12-23
You're welcome.

---

