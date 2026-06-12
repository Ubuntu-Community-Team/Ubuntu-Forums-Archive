---
title: "No sound from 3gp files"
date: 2006-09-05
forum: General Help
---

### Post by th3james on 2006-09-05
Hi

No matter what player i use (mplayer, xine, vlc) nothing will play 3gp files from my sony K750i (or my old samsung d500) with sound. I've been searching around the forums, but i havent found a fix for this, i tried [this]("http://ubuntuforums.org/showthread.php?t=178455&highlight=3gp+sound") howto, but i have the same problem as [this]("http://ubuntuforums.org/showthread.php?t=184410&highlight=3gp+sound") user.
If noone knows of a fix, does anyone know how i can convert the files to a format that will have audio?

Thanks

---

### Post by th3james on 2006-09-05
I managed to build a .deb using checkinstall from the [aformentioned howto]("http://www.ubuntuforums.org/showthread.php?t=178455"), and install it, but it still gives me this error in mplayer

```
cox@thepopemobile:~$ mplayer Desktop/MOV00001.3gp
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium 4/Celeron 4 Northwood; Pentium 4 EE/Xeon Prestonia,Gallatin ( Family: 15, Stepping: 7)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


91 audio & 204 video codecs
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
Playing Desktop/MOV00001.3gp.
ISO: File Type Major Brand: 3GPP Profile 5
Quicktime/MOV file format detected.
--------------
MOV track #0: 155 chunks, 1541 samples
MOV: Found H.263 decoder atom d263 (31)!
MOV: Vendor: EMP  H.263 level: 0 H.263 profile: 45
Image size: 176 x 144 (24 bpp)
Display size: 176 x 144
Fourcc: s263  Codec: ''
--------------
MOV track #1: 155 chunks, 0 samples
Audio bits: 8  chans: 1  rate: 8000
MOV: Found AMR audio atom damr (17)!
MOV: Vendor: EMP  Version: 0
MOV: Modes set: 0080
MOV: Mode change period: 0 Frames per sample: 1
Fourcc: samr
--------------
MOV: longest streams: A: #1 (155 samples)  V: #0 (1541 samples)
VIDEO:  [s263]  176x144  24bpp  1.534 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
Cannot find codec 'amr_nb' in libavcodec...
ADecoder init failed :(
ADecoder init failed :(
Cannot find codec for audio format 0x726D6173.
Read DOCS/HTML/en/codecs.html!
==========================================================================
Xlib:  extension "XFree86-VidModeExtension" missing on display ":0.0".
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh263] vfm: ffmpeg (FFmpeg H.263+ decoder)
==========================================================================
Audio: no sound
Starting playback...
VDec: vo config request - 176 x 144 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 176x144 => 192x144 Planar YV12
V:  24.0 235/235  1%  0%  0.0% 0 0
Exiting... (Quit)
```
Ideally, I'd like to get it working with xine, cuz kaffeine is my preffered player

---

### Post by amr2205 on 2006-09-07
I have installed Realplayer for linux from here:
[http://www.real.com/linux/](http://www.real.com/linux/)
and it works! 3GP videos with sound! \\:D/

---

### Post by th3james on 2006-09-08
It works! Thanks

---

### Post by Paulo Wageck on 2006-09-15
> **th3james said:**
> It works! Thanks

no sound here.. =(((((

---

### Post by Treviño on 2006-09-27
read this: [http://ubuntuforums.org/showpost.php?p=1552286&postcount=141](http://ubuntuforums.org/showpost.php?p=1552286&postcount=141)

---

