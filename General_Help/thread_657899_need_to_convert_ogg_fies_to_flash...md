---
title: "need to convert ogg fies to flash.."
date: 2008-01-04
forum: General Help
---

### Post by Mia_tech on 2008-01-04
I have an .ogg file from my recordmydesktop that I need to convert to .swf

any help appreciated...

---

### Post by Blindraven on 2008-01-04
> **Mia_tech said:**
> I have an .ogg file from my recordmydesktop that I need to convert to .swf

any help appreciated...

Assuming you have[ FFMPEG]("http://ffmpeg.mplayerhq.hu/").
Issue the following command :

```
ffmpeg -i in.ogg -b 384000 -s 640x480 -pass 1 -passlogfile log-file out.flv
```

---

### Post by Mia_tech on 2008-01-04
> **Blindraven said:**
> Assuming you have[ FFMPEG]("http://ffmpeg.mplayerhq.hu/").
Issue the following command :

```
ffmpeg -i in.ogg -b 384000 -s 640x480 -pass 1 -passlogfile log-file out.flv
```

yes, but the previous command is not rendering output in .swf(flash) or am I missing something?

thanks

---

### Post by steeleyuk on 2008-01-04
FLV is the flash video format. SWF is mainly used for vector animations like those produced by Adobe Flash (the animation/drawing program).

I'm not sure if you can convert an OGG video file to SWF...

---

### Post by Vadi on 2008-02-22
> **Blindraven said:**
> Assuming you have[ FFMPEG]("http://ffmpeg.mplayerhq.hu/").
Issue the following command :

```
ffmpeg -i in.ogg -b 384000 -s 640x480 -pass 1 -passlogfile log-file out.flv
```

Thanks, worked for me.

---

### Post by Grugs on 2008-05-19
I have created a file called out.ogg.ogv with recordmydesktop .

To convert this file into a flash video I have then run:

```
ffmpeg -i out.ogg.ogv -b 384000 -s 640x480 -pass 1 -passlogfile log-file out.flv
```

The response is

```
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-liba52 --enable-libdts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul  9 2007 22:27:18, gcc: 4.1.3 20070601 (prerelease) (Debian 4.1.2-12)
[theora @ 0x2ad635d4b190]Theora bitstream version 30201
[theora @ 0x2ad635d4b190]560 bits left in packet 81
[theora @ 0x2ad635d4b190]7 bits left in packet 82
Input #0, ogg, from 'out.ogg.ogv':
  Duration: 00:03:37.4, start: 3.200000, bitrate: 643 kb/s
  Stream #0.0: Video: 0x0000, 1000000.00 fps(r)
  Stream #0.1: Video: theora, yuv420p, 1280x832, 15.00 fps(r)
  Stream #0.2: Audio: vorbis, 44100 Hz, stereo, 64 kb/s
PIX_FMT_YUV420P will be used as an intermediate format for rescaling
Output #0, flv, to 'out.flv':
  Stream #0.0: Video: flv, yuv420p, 640x480, q=2-31, pass 1, 384 kb/s, 15.00 fps(c)
Stream mapping:
  Stream #0.0 -> #0.0
[flv @ 0x2ad635d4b190]removing common factors from framerate
Unsupported codec (id=0) for input stream #0.0
```

:(

---

