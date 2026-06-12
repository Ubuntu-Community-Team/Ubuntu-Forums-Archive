---
title: "mplayer don't playback"
date: 2005-05-21
forum: General Help
---

### Post by flashdog on 2005-05-21
Hello,
I have to install mplayer with synaptic with mozilla-mplayer.
After the installation mplayer will not playback.
Then I try to install mplayer-586 and mplayer-k6, but without success.

```

flashdog@ubuntu:/media/cdrom$ mplayer hallo.avi
MPlayer 1.0pre6-3.3.5 (C) 2000-2004 MPlayer Team
CPU: Advanced Micro Devices Athlon 64 Clawhammer (Family: 8, Stepping: 8)
Detected cache-line size is 64 bytes
MMX2 supported but disabled
SSE supported but disabled
SSE2 supported but disabled
3DNow supported but disabled
3DNowExt supported but disabled
CPUflags:  MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 0 SSE2: 0
Compiled for x86 CPU with extensions: MMX



Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing hallo.avi.
AVI file format detected.
VIDEO:  [DIV3]  432x320  24bpp  25.000 fps  558.7 kbps (68.2 kbyte/s)
Clip info:
 Software: Nandub v1.0rc2
==========================================================================
Trying to force audio codec driver family libmad...
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 44100 Hz, 2 ch, 16 bit (0x10), ratio: 12000->176400 (96.0 kbit)
Selected audio codec: [mad] afm:libmad (libMAD MPEG layer 1-2-3)
==========================================================================
vo: X11 running at 1280x1024 with depth 24 and 32 bpp (":0.0" => local display)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffdivx] vfm:ffmpeg (FFmpeg DivX ;-) (MS MPEG-4 v3))
==========================================================================
Checking audio filter chain for 44100Hz/2ch/16bit -> 44100Hz/2ch/16bit...
AF_pre: af format: 2 bps, 2 ch, 44100 hz, little endian signed int
AF_pre: 44100Hz 2ch Signed 16-bit (Little-Endian)
alsa-init: got device=0, subdevice=0
alsa-init: 1 soundcard found, using: default 

``` 

Then I make Ctrl+C I get:
```

MPlayer interrupted by signal 2 in module: enable_cache


MPlayer interrupted by signal 2 in module: ao2_init 

``` 

Then I make gmplayer I get:
```

$ gmplayer hallo.avi
MPlayer 1.0pre6-3.3.5 (C) 2000-2004 MPlayer Team
CPU: Advanced Micro Devices Athlon 64 Clawhammer (Family: 8, Stepping: 8)
Detected cache-line size is 64 bytes
MMX2 supported but disabled
SSE supported but disabled
SSE2 supported but disabled
3DNow supported but disabled
3DNowExt supported but disabled
CPUflags:  MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 0 SSE2: 0
Compiled for x86 CPU with extensions: MMX




vo: X11 running at 1280x1024 with depth 24 and 32 bpp (":0.0" => local display)
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing /media/cdrom0/hallo.avi.
Cache fill:  0.00% (0 bytes)    AVI file format detected.
VIDEO:  [DIV3]  432x320  24bpp  25.000 fps  558.7 kbps (68.2 kbyte/s)
Clip info:
 Software: Nandub v1.0rc2
==========================================================================
Trying to force audio codec driver family libmad...
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 44100 Hz, 2 ch, 16 bit (0x10), ratio: 12000->176400 (96.0 kbit)
Selected audio codec: [mad] afm:libmad (libMAD MPEG layer 1-2-3)
==========================================================================
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffdivx] vfm:ffmpeg (FFmpeg DivX ;-) (MS MPEG-4 v3))
==========================================================================
Checking audio filter chain for 44100Hz/2ch/16bit -> 44100Hz/2ch/16bit...
AF_pre: af format: 2 bps, 2 ch, 44100 hz, little endian signed int
AF_pre: 44100Hz 2ch Signed 16-bit (Little-Endian)
alsa-init: got device=0, subdevice=0
alsa-init: 1 soundcard found, using: default 

``` 

Then I make Ctrl+C I get:
```

[ws] Error in display.
[ws]  Error code: 169 ( BadShmSeg (invalid shared segment parameter) )
[ws]  Request code: 146
[ws]  Minor code: 2
[ws]  Modules: enable_cache 

```

---

### Post by f.prisson on 2005-05-21
Ubuntu uses the esound daemon (esd) as default. You have to enable it in mplayer (Preferences -> Audio -> ESD).

---

### Post by flashdog on 2005-05-22
Thanks! Mplayer can now playback.

---

