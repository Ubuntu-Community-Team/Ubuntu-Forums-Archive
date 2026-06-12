---
title: "Gv4l"
date: 2005-05-16
forum: General Help
---

### Post by Jagec on 2005-05-16
Is there any automated way to install Gv4l program on Ubuntu? I tryed to installed it with apt and manually and it does not work, and it's the only descent program for capturing I found. It worked perfectly on Slack, but I switched to Ubuntu recently. Anyway, here's the Transcode output:

transcode v0.6.14 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg 
[probe_v4l] cannot (reopen) device in RW mode 
[probe_v4l] open video4linux device: Cannot allocate memory 
tc_memcpy: using mmxext for memcpy 
[import_v4l.so] v0.0.5 (2003-06-11) (video) v4l | (audio) PCM 
Xv: NV Video Overlay: ports 61 - 61 
Xv: grabbed port 61 
Using Xv for display 
[export_ffmpeg.so] v0.3.13 (2004-08-03) (video) FFmpegcvsb4731 | (audio) MPEG/AC3/PCM 
[filter.c] Filter "yuy2toyv12" with args (yuy2toyv12) 
[filter.c] Filter "yuy2toyv12" not loaded. Loading ... 
[filter.c] Loading (yuy2toyv12) .. 
[export_ffmpeg.so] Using FFMPEG codec 'mjpeg' (FourCC 'MJPG', Motion JPEG). 
[export_ffmpeg.so]: WARNING: Interlacing parameters unknown, use --encode_fields 
[export_ffmpeg.so]: INFO: No profile selected 
[export_ffmpeg.so] Neither './ffmpeg.cfg' nor '~/.transcode/ffmpeg.cfg' 
[export_ffmpeg.so] found. Default settings will be used instead. 
[export_ffmpeg.so]: INFO: Starting 1 thread(s) 
[export_ffmpeg.so]: INFO: Set display aspect ratio to input 
[mjpeg @ 0xa41c5008]colorspace not supported in jpeg 
[export_ffmpeg.so] could not open FFMPEG codec 
[transcode] warning : (encoder.c) video export module error: init failed 
[transcode] auto-probing source /dev/video0 (failed) 
[transcode] V: import format | unknown (V=v4l|A=(null)) 
[transcode] V: import frame | 720x576 1.25:1  
[transcode] V: de-interlace | (mode=5) interpolate scanlines / blend frames 
[transcode] V: bits/pixel | 0.174 
[transcode] V: decoding fps,frc | 25.000,3 
[transcode] V: Y'CbCr | YV12/I420 
[transcode] A: import format | 0x2000 AC3 [48000,16,2] 
[transcode] A: export format | 0x55 MPEG layer-3 [48000,16,2] 128 kbps 
[transcode] V: encoding fps,frc | 25.000,3 
[transcode] A: bytes per frame | 7680 (7680.000000) 
[transcode] A: adjustment | 0@1000 
[transcode] V: IA32 accel mode | sse (sse 3dnowext 3dnow mmxext mmx asm C) 
[transcode] V: video buffer | 100 @ 720x576 
[filter_pv.so] v0.2.3 (2004-06-01) xv only preview plugin 
[filter_pv.so] preview window 720x576 
[import_v4l.so] video4linux audio grabbing 
(audio.c) audio blocksize 4096 
[import_v4l.so] video4linux video grabbing 
(video.c) Television: has[ PAL NTSC SECAM ] is[ PAL ] 
(video.c) "RTL": using .xawtv from /home/ijagec, freq=503.25MHZ 
(video.c) europe-east: station=RTL bright=50% contrast=50% color=50% hue=50% 
(video.c) Television: input #0, tuner tv  
(video.c) (audio-audio): muted=no volume=87% bass= 0% treble= 0% 
(video.c) picture: brightness=50% hue=50% colour=50% contrast=50% 
(video.c) setattr: setting bright to 32768 (50%). 
(video.c) setattr: setting contrast to 32768 (50%). 
(video.c) setattr: setting color to 32768 (50%). 
(video.c) setattr: setting hue to 32768 (50%). 
[filter_yuy2tov12.so] v0.0.2 (2003-09-04) YUY2 to YV12 converter plugin 
(video.c) 4 frame buffer(s) available 
(video.c) video device OK - recording from [RTL] 
(video.c) recording limited to 1 frames. 
[import_v4l.so] dropping 25 video frames for AV sync 
[transcode] critical: failed to init encoder 

Any help yould be highly appreciated, and I would like to make a proposal for incloude that program in next Ubuntu release.

Thank you.

---

### Post by zeroconf on 2005-11-10
I have also problems with GV4L. I use Edubuntu 5.10.

```
root@edubuntu:~# dpkg -i /home/user/soft/gv4l-2.2.4-i386.deb
dpkg: regarding .../soft/gv4l-2.2.4-i386.deb containing gv4l, pre-dependency problem:
 gv4l pre-depends on libbonobo-activation4 (>= 1:2.2.4)
dpkg: error processing /home/user/soft/gv4l-2.2.4-i386.deb (--install):
 pre-dependency problem - not installing gv4l
Errors were encountered while processing:
 /home/user/soft/gv4l-2.2.4-i386.deb

root@edubuntu:~# apt-get install libbonobo-activation4
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  transcode: Depends: libfame-0.9 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

root@edubuntu:~# apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libfame-0.9
The following NEW packages will be installed:
  libfame-0.9
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
1 not fully installed or removed.
Need to get 0B/77.7kB of archives.
After unpacking 319kB of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
(Reading database ... 92928 files and directories currently installed.)
Unpacking libfame-0.9 (from .../libfame-0.9_0.9.0-0.1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libfame-0.9_0.9.0-0.1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libfame-0.9.so.0.0.0', which is also in package libfame0
Errors were encountered while processing:
 /var/cache/apt/archives/libfame-0.9_0.9.0-0.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

root@edubuntu:~# apt-get remove libfame0
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  transcode: Depends: libfame-0.9 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@edubuntu:~#

```

I even removed those libraries - libfame-0.9.so.0.0.0 and symlink for it but still nothing.

My /etc/apt/sources.list:
```

deb http://ee.archive.ubuntu.com/ubuntu breezy main restricted universe multiverse
deb-src http://ee.archive.ubuntu.com/ubuntu breezy main restricted universe multiverse
deb http://ee.archive.ubuntu.com/ubuntu breezy-security main restricted universe multiverse
deb-src http://ee.archive.ubuntu.com/ubuntu breezy-security main restricted universe multiverse
deb http://ee.archive.ubuntu.com/ubuntu/ breezy-updates main restricted universe multiverse
deb-src http://ee.archive.ubuntu.com/ubuntu/ breezy-updates main restricted universe multiverse
deb ftp://cipherfunk.org/pub/packages/ubuntu breezy main

```

What shall I do? I needed program to save webcam video and TV-shows, too. I already thought taht Edubuntu does it.

---

### Post by suoko on 2005-11-21
Try installing attached db file.
It's the alienized rpm from sourceforge

---

