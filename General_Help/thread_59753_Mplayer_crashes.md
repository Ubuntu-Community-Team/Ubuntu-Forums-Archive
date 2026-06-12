---
title: "Mplayer crashes"
date: 2005-08-25
forum: General Help
---

### Post by BanskuZ on 2005-08-25
Mplayer crashed, when I was trying to watch video:
```
Playing /mnt/windows/********/*******/*********.avi.
AVI file format detected.
VIDEO:  [XVID]  640x272  12bpp  25,000 fps  1239,0 kbps (151,2 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.4.1 (build 2178/release)
==========================================================================
Trying to force audio codec driver family libmad...
Opening audio decoder: [liba52] AC3 decoding with liba52
AC3: 5.1 (3f+2r+lfe)  48000 Hz  448,0 kbit/s
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, 16 bit (0x10), ratio: 56000->192000 (448,0 kbit)
Selected audio codec: [a52] afm:liba52 (AC3-liba52)
==========================================================================
==========================================================================
Trying to force video codec driver family vfw...
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm:ffmpeg (FFmpeg MPEG-4)
==========================================================================
Checking audio filter chain for 48000Hz/2ch/16bit -> 48000Hz/2ch/16bit...
AF_pre: af format: 2 bps, 2 ch, 48000 hz, little endian signed int
AF_pre: 48000Hz 2ch Signed 16-bit (Little-Endian)
alsa-init: got device=0, subdevice=0
alsa-init: 1 soundcard found, using: default
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch Signed 16-bit (Little-Endian) (2 bps)
Building audio filter chain for 48000Hz/2ch/16bit -> 48000Hz/2ch/16bit...
Starting playback...


MPlayer interrupted by signal 11 in module: decode_audio
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
alsa-uninit: pcm closed
```
Gxine, VLC or Kaffeine works fine.  ](*,)

---

### Post by clehel on 2005-08-25
I got similar crash when trying to play a DVD:
"MPlayer interrupted by signal 11 in module: decode_audio"

In my case also, vlc and Kaffeine work.

---

### Post by bob k on 2005-08-25
I gave up on mplayer for this release. The plugin dosen't work right, and after that there are other programs that work better than mplayer for DVD and CDs. Unless you have a format that wont work with anything else, then try mplayer.

---

