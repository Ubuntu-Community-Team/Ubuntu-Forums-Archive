---
title: "No aac support in ffmpeg?"
date: 2006-12-23
forum: General Help
---

### Post by kd7swh on 2006-12-23
How do I get aac encoding support in ffmpeg? I have faac and faad installed but I get this:


FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Sep 20 2006 00:26:15, gcc: 4.1.2 20060906 (prerelease) (Ubuntu 4.1.1-13ubuntu2)
Input #0, avi, from '/home/usr/test.avi':
  Duration: 00:21:55.8, start: 0.000000, bitrate: 925 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 512x384, 23.98 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 160 kb/s
[COLOR="Red"]Unknown codec 'aac'[/COLOR]

why is the codec "unknown"?](*,)


was the deb not built with aac support?????

---

### Post by pay on 2006-12-23
> **kd7swh said:**
> was the deb not built with aac support?????I don't know for sure but Ubuntu normally stay clear from restrictive formats like aac. What you probably need to do is install libfaac-dev, and then compile ffmpeg

---

### Post by kd7swh on 2006-12-23
The libraries needed are installed, i think.  I have tried compiling from source but it keeps telling me it can't find some dependencies that I know are already installed. What Directory should I be compiling ffmpeg in so it can find what it needs to properly compile with aac support?


and I already knew the deb was not built with aac support, I just rhetorically stated that out of frustration.

---

### Post by pay on 2006-12-23
The dependencies that you need to compile ffmpeg with aac support are the faac dev packages.

---

### Post by Sef on 2006-12-23
Thread locked.  Duplicate Thread.   For [Posting]("http://ubuntuforums.org/showthread.php?t=324394").

---

