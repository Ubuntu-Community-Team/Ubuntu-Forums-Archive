---
title: "unsupported codec for ffmpeg"
date: 2006-11-13
forum: General Help
---

### Post by Westerberg on 2006-11-13
trying to convert a VOB file to AVI
results in unsupported audio codec error message
```
echo "PASS ONE using ffmpeg"
ffmpeg -i movies-001.vob -f avi -vcodec mpeg4 -b 768 -g 384 -bf 2 -deinterlace -an -pass 1 -passlogfile fftmp.log fftmp.avi
echo "PASS TWO using ffmpeg"
ffmpeg -i movies-001.vob -y -f avi -vcodec mpeg4 -b 768 -g 384 -bf 2 -deinterlace -ar 44100 -ab 128 -acodec mp3 -pass 2 -passlogfile fftmp.log brokenflowers.avi
```
results in:
```
PASS ONE using ffmpeg
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --extra-cflags=-fomit-frame-pointer -DRUNTIME_CPUDETECT --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
  built on Oct  4 2006 10:57:36, gcc: 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
Input #0, mpeg, from 'movies-001.vob':
  Duration: 00:16:14.0, start: 0.280633, bitrate: 8818 kb/s
  Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480, 29.97 fps, 9800 kb/s
  Stream #0.1[0x80]: Audio: ac3, 48000 Hz, 5:1, 448 kb/s
  Stream #0.2[0x20]: Subtitle: dvdsub
File 'fftmp.avi' already exists. Overwrite ? [y/N] n
Not overwriting - exiting
PASS TWO using ffmpeg
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --extra-cflags=-fomit-frame-pointer -DRUNTIME_CPUDETECT --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
  built on Oct  4 2006 10:57:36, gcc: 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
Input #0, mpeg, from 'movies-001.vob':
  Duration: 00:16:14.0, start: 0.280633, bitrate: 8818 kb/s
  Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480, 29.97 fps, 9800 kb/s
  Stream #0.1[0x80]: Audio: ac3, 48000 Hz, 5:1, 448 kb/s
  Stream #0.2[0x20]: Subtitle: dvdsub
Output #0, avi, to 'brokenflowers.avi':
  Stream #0.0: Video: mpeg4, yuv420p, 720x480, 29.97 fps, q=2-31, pass 2, 768 kb/s
  Stream #0.1: Audio: 0x0000, 44100 Hz, stereo, 128 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec for output stream #0.1

```
any ideas what i need to do to resolve this?

---

