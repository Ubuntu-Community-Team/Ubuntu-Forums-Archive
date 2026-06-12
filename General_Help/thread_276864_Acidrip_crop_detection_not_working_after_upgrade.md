---
title: "Acidrip crop detection not working after upgrade"
date: 2006-10-13
forum: General Help
---

### Post by ixus_123 on 2006-10-13
i upgraded acidrip and after a system update it fails to crop detect to remove black bars on video.

It will still find teh DVD, read chapters, & play previews.

Anyonne have any idea how to fix please?

[IMG]http://img.photobucket.com/albums/v284/ixus_123/screenshots/acidrip-crop.jpg[/IMG]

---

### Post by hotani on 2006-10-13
Same problem here, no idea how to fix it. I was just about to say acidrip is now functional since a recent update fixed the ":bitrate" bug, but it seems to have been replaced with this one. :(

Probably unrelated, but for the past several rips the colors have been horribly off in any xine-based player. Big green bar across the top and all colors out of whack all through the video. It works in everything else, and I had to change totem back to gstreamer so I could watch my movies.

---

### Post by ixus_123 on 2006-10-13
I'm getting a thin green bar along the bottom but current;y backing up a TV series DVD & although cropping doesn't work it seems to have cropped anyway.

Just installed x264 video codec & I'm amazed at the compression.  I'm doing full size video at the same bitrate & it's less than hald the size of an xvid rip.  It does seem a bit blokier though so I think I'll have to push bit rate  way up.  I've been a bit conservative up till now as it's predicting file sizes about 4 times as large.

I someone can help - I much prefer acidrip over dvdrip - I can queue up items & just click & go

---

### Post by hotani on 2006-10-14
Having just moved to Ubuntu from OSX, [Handbrake](http://handbrake.m0k.org/) is one of the few things I *really* miss. acidrip is still a bit flaky. Handbrake will run on Linux but I believe it needs to be compiled and I haven't been that motivated yet.

---

### Post by ixus_123 on 2006-10-14
I'd never heard of HandBrake - thanks.

Just downloaded it, unpacked it with file-roller & installing is as easy as CDing to the directory
./configure
jam


- not sure what jam is - I had to apt-get it but it's taking ages - about 5 minutes now of compiling & downloading stuff.

Just found out HandBrake has no GUI on Linux & has to be run from the comand line so although I'm installing it now, I doubt I'll use it

---

### Post by aseneca on 2006-10-22
if you look at the config files for the program you can fix the error... however... you have to manually enter the values into the software; the values will appear in the debug window as the movie plays.. You can stop it after a while ..

I emailed the author of this software.. let see if he fully corrects the problem in its next release...

mmm

---

### Post by WamBamBoozle on 2006-10-25
What fixed this for me was to install upgradable packages, one of which included mplayer.

[LIST=1]
[*]System->Administration->Synaptic Package Manager
[*]select the "status" button on the bottom left
[*]select the "Installed (upgradable)" in the upper left
[/LIST]

Then when acidrip attempts to detect cropping, it gets the data it needs in

AcidRip message - AcidRip 0.14, "Written" by C.Phillips <acid_kewpie@users.sf.net>

...

AcidRip message - Crop detection in progress... please wait
AcidRip message - Running mplayer -vf cropdetect dvd://1 -dvd-device /dev/dvd -nosound -vo null -frames 10 -sstep 277 -nocache
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3000+ (Family: 15, Model: 47, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Terminal type `unknown' is not defined.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.

Playing dvd://1.
Reading disc structure, please wait...
There are 7 titles on this DVD.
There are 37 chapters in this DVD title.
There are 1 angles in this DVD title.
DVD successfully opened.
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 3)  29.970 fps  9800.0 kbps (1225.0 kbyte/s)
Opening video filter: [cropdetect]
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
Opening video filter: [lavc]
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Audio: no sound
Starting playback...
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
[mpeg1video @ 0xcae5b0]removing common factors from framerate
VO: [null] 720x480 => 854x480 Mpeg PES 
V:   0.0   1/  1 ??% ??% ??,?% 0 0                                              
V:   0.2   2/  2 ??% ??% ??,?% 0 0                                              
V: 281.2   3/  3 ??% ??% ??,?% 0 0                                              
V: 443.9   4/  4 ??% ??% ??,?% 0 0                                              
[CROP] Crop area: X: 58..695  Y: 58..417  (-vf crop=624:352:66:62).
V: 567.1   6/  5 ??% ??% ??,?% 0 0                                              
[CROP] Crop area: X: 0..718  Y: 58..417  (-vf crop=704:352:8:62).
V: 677.8   7/  6 ??% ??% ??,?% 0 0                                              
[CROP] Crop area: X: 0..718  Y: 58..417  (-vf crop=704:352:8:62).
V: 770.4   9/  7 ??% ??% ??,?% 0 0                                              
[CROP] Crop area: X: 0..718  Y: 58..417  (-vf crop=704:352:8:62).
V: 848.9  10/  8 ??% ??% ??,?% 0 0                                              
[CROP] Crop area: X: 0..718  Y: 58..417  (-vf crop=704:352:8:62).
V: 932.1  11/  9 ??% ??% ??,?% 0 0                                              
[CROP] Crop area: X: 0..718  Y: 58..417  (-vf crop=704:352:8:62).
V:1012.7  12/ 10 ??% ??% ??,?% 0 0                                              
[CROP] Crop area: X: 0..718  Y: 58..417  (-vf crop=704:352:8:62).
V:1089.0  13/ 11 ??% ??% ??,?% 0 0                                              
[CROP] Crop area: X: 0..718  Y: 58..417  (-vf crop=704:352:8:62).
V:1161.6  14/ 12 ??% ??% ??,?% 0 0                                              


Exiting... (End of file)
AcidRip message - Crop detection completed

---

### Post by ixus_123 on 2006-10-25
Thanks for replying :)
I am updated to all te latest packages on teh dapper repos. Are you on dapper or did you upgrade mplayer to efty?

this is what I got just now from the debug window

```
AcidRip message - Crop detection in progress... please wait
AcidRip message - Running mplayer -vf cropdetect dvd://1 -dvd-device /dev/dvd -nosound -vo null -frames 10 -sstep 257 -nocache
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices  (Family: 15, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


91 audio & 204 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Terminal type `unknown' is not defined.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing dvd://1.
libdvdread: Using libdvdcss version 1.2.9 for DVD access
Reading disc structure, please wait...
There are 19 titles on this DVD.
There are 37 chapters in this DVD title.
There are 1 angles in this DVD title.

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0001f640
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0001fc14
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0007e6e3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0007fb80
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0037ff94
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 0
DVD successfully opened.
MPEG-PS file format detected.
VIDEO:  MPEG2  720x576  (aspect 3)  25.000 fps  7500.0 kbps (937.5 kbyte/s)
Opening video filter: [cropdetect]
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
Opening video filter: [lavc]
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Audio: no sound
Starting playback...
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [null] 720x576 => 1024x576 Mpeg PES 
V:   0.0   1/  1 ??% ??% ??,?% 0 0                                              
V:   0.1   2/  2 ??% ??% ??,?% 0 0                                              
V: 264.9   3/  3 ??% ??% ??,?% 0 0                                              
V: 391.0   4/  4 ??% ??% ??,?% 0 0                                              
crop area: X: 2..716  Y: 0..575  (-vf crop=704:576:8:0)
V: 504.4   5/  5 ??% ??% ??,?% 0 0                                              
crop area: X: 2..717  Y: 0..575  (-vf crop=704:576:8:0)
V: 604.0   6/  6 ??% ??% ??,?% 0 0                                              
crop area: X: 2..717  Y: 0..575  (-vf crop=704:576:8:0)
V: 693.4   7/  7 ??% ??% ??,?% 0 0                                              
crop area: X: 2..717  Y: 0..575  (-vf crop=704:576:8:0)
V: 774.3   8/  8 ??% ??% ??,?% 0 0                                              
crop area: X: 2..717  Y: 0..575  (-vf crop=704:576:8:0)
V: 846.9   9/  9 ??% ??% ??,?% 0 0                                              
crop area: X: 2..717  Y: 0..575  (-vf crop=704:576:8:0)
V: 918.3  10/ 10 ??% ??% ??,?% 0 0                                              
crop area: X: 2..717  Y: 0..575  (-vf crop=704:576:8:0)
V: 984.9  11/ 11 ??% ??% ??,?% 0 0                                              
crop area: X: 2..717  Y: 0..575  (-vf crop=704:576:8:0)
V:1037.7  12/ 12 ??% ??% ??,?% 0 0                                              


Exiting... (End of file)
AcidRip message - Crop detection failed, is the DVD loaded?


```

---

### Post by WamBamBoozle on 2006-10-29
Yes. I'm running edgy eft. On amd 64

acidrip_0.14-0.2ubuntu4

Package: mplayer
Binary: mplayer-doc, mplayer-nogui, mencoder, mplayer
Version: 2:0.99+1.0pre8-0ubuntu8

The output you're getting from mplayer will not be parsed by acidrip. It is looking for patterns that start with CROP

It occurs to me that one hack you could do is change pattern acidrip is looking for. I don't know if you want to dig that deep.

Or you could be like me and upgrade to edgy eft.

---

### Post by hotani on 2006-10-30
Yep - same here. Upgraded to Edgy and crop detection works again.

---

