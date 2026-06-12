---
title: "self-compiled mplayer wont play mpg's"
date: 2007-01-21
forum: General Help
---

### Post by nix4me on 2007-01-21
Hi,

I compiled mplayer from svn code and it works great for the most part except 1 thing.

When i try to play mpg's with gmplayer (the gui version) they skip and dont play.  However, when i play them with mplayer (non-gui) they play fine.

Here is the output i get form the command line when trying with gmplayer:

```
MPlayer dev-SVN-r21970-4.1.2 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.80GHz (Family: 15, Model: 3, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/Arial_Black.ttf doesn't look like a bitmap font description, ignoring.
Cannot load bitmap font: /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/Arial_Black.ttf
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/nix4me/Desktop/03_ZX-6_Streets.mpg.
MPEG-PS file format detected.
VIDEO:  MPEG1  320x240  (aspect 1)  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Trying to force video codec driver family ffmpeg...
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffmpeg1] vfm: ffmpeg (FFmpeg MPEG-1)
==========================================================================
==========================================================================
Trying to force audio codec driver family ffmpeg...
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
[mp2 @ 0x894abd8]incorrect frame size
AUDIO: 32000 Hz, 1 ch, s16le, 32.0 kbit/6.25% (ratio: 4000->64000)
Selected audio codec: [ffmp2] afm: ffmpeg (FFmpeg MPEG layer-1 and layer-2 audio decoder)
==========================================================================
AO: [alsa] 48000Hz 1ch s16le (2 bytes per sample)
Starting playback...
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
VDec: vo config request - 320 x 240 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 320x240 => 320x240 Planar YV12 
[mp2 @ 0x894abd8]incorrect frame size000   1/  1 ??% ??% ??,?% 0 0                                                   
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size004   2/  2 ??% ??% ??,?% 1 0                                                   
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size008   3/  3 ??% ??% ??,?% 2 0                                                   
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size012   4/  4 ??% ??% ??,?% 3 0                                                   
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size016   5/  5 ??% ??% ??,?% 4 0                                                   
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
```

Anyone have any ideas why its doing this?

Thanks,
nix4me

---

