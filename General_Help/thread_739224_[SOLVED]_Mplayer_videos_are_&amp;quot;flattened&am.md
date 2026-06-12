---
title: "[SOLVED] Mplayer videos are &amp;quot;flattened&amp;quot;"
date: 2008-03-29
forum: General Help
---

### Post by akudewan on 2008-03-29
I upgraded my computer a couple of days ago, and installed Ubuntu (Gutsy) from scratch. Everything works like a charm.

I use mplayer-nogui to play videos, and the videos appear "flattened", as though the aspect ratio is messed up. The aspect ratio of my monitor is 16:10 and I've set the "widescreen" option in "Screens and Graphics".

This problem is only with mplayer. Totem can play just fine, and the video appears properly.

Does anyone know how to fix this ?

Output given by mplayer :-
```

MPlayer 2:1.0~rc1-0ubuntu13.2 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz (Family: 6, Model: 15, Stepping: 11)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Naruto Shippuuden 044.avi.
AVI file format detected.
AVI: ODML: Building ODML index (2 superindexchunks).
VIDEO:  [XVID]  640x480  12bpp  23.976 fps  898.2 kbps (109.6 kbyte/s)
Clip info:
 Software: Windows Movie Maker 2.1
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 640 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 640x480 => 640x480 Planar YV12 
gnome_screensaver_control()00 ct:  0.093 16318/16318  2%  0%  0.9% 0 0 
Exiting... (Quit)
akudewan@ranjandesk:~/Naruto$ totem Naruto\ Shippuuden\ 044.avi 
sh: jackd: not found
sh: jackd: not found
akudewan@ranjandesk:~/Naruto$ totem Naruto\ Shippuuden\ 044.avi 
sh: jackd: not found
sh: jackd: not found
akudewan@ranjandesk:~/Naruto$ mplayer Naruto\ Shippuuden\ 044.avi 
MPlayer 2:1.0~rc1-0ubuntu13.2 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz (Family: 6, Model: 15, Stepping: 11)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Naruto Shippuuden 044.avi.
AVI file format detected.
AVI: ODML: Building ODML index (2 superindexchunks).
VIDEO:  [XVID]  640x480  12bpp  23.976 fps  898.2 kbps (109.6 kbyte/s)
Clip info:
 Software: Windows Movie Maker 2.1
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 640 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 640x480 => 640x480 Planar YV12 
gnome_screensaver_control()01 ct:  0.000  62/ 62  5%  0%  1.4% 0 0 
Exiting... (Quit)

```

---

### Post by akudewan on 2008-03-29
No problem I found a fix.

Simply had to add:
**monitoraspect=1440/900**
to ~/.mplayer/config

:)

---

