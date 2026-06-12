---
title: "Converting .flv video file to .avi"
date: 2013-10-26
forum: General Help
---

### Post by t0p on 2013-10-26
I want to convert a .flv format video file to .avi format.

I tried a ffmpeg command:
```

t0p@mars:~/Downloads$ ffmpeg -i Bowling\ For\ Columbine.avi.flv Bowling\ For\ Columbine.avi
ffmpeg version 0.8.6-4:0.8.6-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Apr  2 2013 17:02:36 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[flv @ 0x140e9c0] Estimating duration from bitrate, this may be inaccurate

Seems stream 0 codec frame rate differs from container frame rate: 47.95 (5994/125) -> 23.98 (24000/1001)
Input #0, flv, from 'Bowling For Columbine.avi.flv':
  Metadata:
    metadatacreator : Yet Another Metadata Injector for FLV - Version 1.4
    hasKeyframes    : true
    hasVideo        : true
    hasAudio        : true
    hasMetadata     : true
    canSeekToEnd    : true
    datasize        : 438084397
    videosize       : 347466678
    audiosize       : 88735963
    lasttimestamp   : 7066
    lastkeyframetimestamp: 7066
    lastkeyframelocation: 438110807
  Duration: 01:57:45.56, start: 0.084000, bitrate: 488 kb/s
    Stream #0.0: Video: h264 (High), yuv420p, 576x304, 391 kb/s, 23.98 tbr, 1k tbn, 47.95 tbc
    Stream #0.1: Audio: aac, 44100 Hz, stereo, s16, 96 kb/s
[buffer @ 0x1e0ada0] w:576 h:304 pixfmt:yuv420p
Incompatible sample format 's16' for codec 'ac3', auto-selecting format 'flt'
[ac3 @ 0x1e06340] invalid bit rate
Output #0, avi, to 'Bowling For Columbine.avi':
    Stream #0.0: Video: mpeg4, yuv420p, 576x304, q=2-31, 200 kb/s, 90k tbn, 23.98 tbc
    Stream #0.1: Audio: ac3, 44100 Hz, stereo, flt, 200 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Error while opening encoder for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height

```

It did create a file, Bowling For Columbine.avi, but the file's size was 0 bytes.  This is annoying: I've successfully used ffmpeg for conversion before.

Can anyone fix me up a simple way to do the conversion?

Cheers.

---

### Post by philinux on 2013-10-26
This came to mind. I bookmarked it a while back but not tried it yet though.

[http://iloveubuntu.net/convert-music-videos-pictures-and-isos-format-junkie-powerful-all-one-utility](http://iloveubuntu.net/convert-music-videos-pictures-and-isos-format-junkie-powerful-all-one-utility)

We are spoilt for choice. [http://askubuntu.com/questions/27864/best-video-converter](http://askubuntu.com/questions/27864/best-video-converter)

---

### Post by The Spectre on 2013-10-26
VLC can Transcode video from one format to another...
[https://wiki.videolan.org/Transcode/](https://wiki.videolan.org/Transcode/)

Or if you don't want to install anything on your computer you could try this...
[http://www.clipconverter.cc/](http://www.clipconverter.cc/)

---

### Post by t0p on 2013-10-26
Thanks for suggestions, I'll try them later.I will then return, to tell the forum what worked/didn't work,

---

### Post by FakeOutdoorsman on 2013-10-26
> **t0p said:**
> I want to convert a .flv format video file to .avi format.

I tried a ffmpeg command:
```

t0p@mars:~/Downloads$ ffmpeg -i Bowling\ For\ Columbine.avi.flv Bowling\ For\ Columbine.avi
ffmpeg version 0.8.6-4:0.8.6-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Apr  2 2013 17:02:36 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***

```
Using the buggy and fake "ffmpeg" from libav is often an exercise in time wastage.

Please simply download a recent [Linux build of ffmpeg](http://ffmpeg.org/download.html#LinuxBuilds) (just download, extract, and run), or follow a [step-by-step guide to compile ffmpeg](http://trac.ffmpeg.org/wiki/UbuntuCompilationGuide).

I must ask: why AVI? It's a graybeard container format with much better and modern alternatives (mkv, mp4, etc).

---

