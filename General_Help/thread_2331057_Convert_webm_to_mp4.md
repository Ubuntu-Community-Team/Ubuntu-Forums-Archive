---
title: "Convert webm to mp4"
date: 2016-07-17
forum: General Help
---

### Post by 4kh3RAm on 2016-07-17
I can not figure out how to use ffmpeg to convert webm files to mp4.

I tried this, but it produces an empty file.

```
ffmpeg -i 2016-07-17-215009.webm  your_outfile_name.mp4
```

---

### Post by vasa1 on 2016-07-18
Can you tell us your version of ffmpeg?

And does providing the full path for the input file help?

I have```
$ apt-cache policy ffmpeg
ffmpeg:
  Installed: 7:3.0.0+git1~trusty
  Candidate: 7:3.0.0+git1~trusty
  Version table:
 *** 7:3.0.0+git1~trusty 100
        100 /var/lib/dpkg/status
     7:2.8.6-1ubuntu2 500
        500 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
$ 
```
Your command works for me.

---

### Post by 4kh3RAm on 2016-07-18
> ffmpeg version 2.8.6-1ubuntu2 

Putting in full path made no difference nor did running it in the dir file was in.

---

### Post by &amp;KyT$0P# on 2016-07-18
Can you please post the full output of ffmpeg when you run the command?

---

### Post by Yellow Pasque on 2016-07-18
What happens if you specify what codecs you want to convert to rather than letting ffmpeg guess?

---

### Post by 4kh3RAm on 2016-07-18
> **halogen2 said:**
> Can you please post the full output of ffmpeg when you run the command?

Sure.

```
andy@7:~/Videos/Webcam$ ffmpeg -i 2016-07-17-215009.webm  your_outfile_name.mp4
ffmpeg version 2.8.6-1ubuntu2 Copyright (c) 2000-2016 the FFmpeg developers
  built with gcc 5.3.1 (Ubuntu 5.3.1-11ubuntu1) 20160311
  configuration: --prefix=/usr --extra-version=1ubuntu2 --build-suffix=-ffmpeg --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --cc=cc --cxx=g++ --enable-gpl --enable-shared --disable-stripping --disable-decoder=libopenjpeg --disable-decoder=libschroedinger --enable-avresample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmodplug --enable-libmp3lame --enable-libopenjpeg --enable-libopus --enable-libpulse --enable-librtmp --enable-libschroedinger --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxvid --enable-libzvbi --enable-openal --enable-opengl --enable-x11grab --enable-libdc1394 --enable-libiec61883 --enable-libzmq --enable-frei0r --enable-libx264 --enable-libopencv
  libavutil      54. 31.100 / 54. 31.100
  libavcodec     56. 60.100 / 56. 60.100
  libavformat    56. 40.101 / 56. 40.101
  libavdevice    56.  4.100 / 56.  4.100
  libavfilter     5. 40.101 /  5. 40.101
  libavresample   2.  1.  0 /  2.  1.  0
  libswscale      3.  1.101 /  3.  1.101
  libswresample   1.  2.101 /  1.  2.101
  libpostproc    53.  3.100 / 53.  3.100
Input #0, matroska,webm, from '2016-07-17-215009.webm':
  Metadata:
    encoder         : GStreamer matroskamux version 1.8.1
    creation_time   : 2016-07-18 02:50:10
  Duration: 00:00:08.47, start: 0.000000, bitrate: 3223 kb/s
    Stream #0:0(eng): Video: vp8, yuv420p, 1280x720, SAR 1:1 DAR 16:9, 250 tbr, 1k tbn, 1k tbc (default)
    Metadata:
      title           : Video
    Stream #0:1(eng): Audio: vorbis, 44100 Hz, mono, fltp (default)
    Metadata:
      title           : Audio
[libx264 @ 0x1134820] using SAR=1/1
[libx264 @ 0x1134820] using cpu capabilities: MMX2 SSE2Fast SSSE3 SSE4.2 AVX XOP FMA4 FMA3 LZCNT BMI1
[libx264 @ 0x1134820] profile High, level 5.1
[libx264 @ 0x1134820] 264 - core 148 r2643 5c65704 - H.264/MPEG-4 AVC codec - Copyleft 2003-2015 - http://www.videolan.org/x264.html - options: cabac=1 ref=3 deblock=1:0:0 analyse=0x3:0x113 me=hex subme=7 psy=1 psy_rd=1.00:0.00 mixed_ref=1 me_range=16 chroma_me=1 trellis=1 8x8dct=1 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=-2 threads=6 lookahead_threads=1 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=3 b_pyramid=2 b_adapt=1 b_bias=0 direct=1 weightb=1 open_gop=0 weightp=2 keyint=250 keyint_min=25 scenecut=40 intra_refresh=0 rc_lookahead=40 rc=crf mbtree=1 crf=23.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 ip_ratio=1.40 aq=1:1.00
[aac @ 0x113ad20] The encoder 'aac' is experimental but experimental codecs are not enabled, add '-strict -2' if you want to use it.




```

---

### Post by &amp;KyT$0P# on 2016-07-18
Looks lke it's trying to encode the audio with 'aac' but has only experimental codec for that.  Does it work if you enable it to be used?
```
ffmpeg -strict -2 -i 2016-07-17-215009.webm  your_outfile_name.mp4
```

---

### Post by leunam12 on 2016-07-18
Did you try avconv or winff (a frontend for avconv)?

---

### Post by 4kh3RAm on 2016-07-18
> **halogen2 said:**
> Looks lke it's trying to encode the audio with 'aac' but has only experimental codec for that.  Does it work if you enable it to be used?
```
ffmpeg -strict -2 -i 2016-07-17-215009.webm  your_outfile_name.mp4
```

How would I do that ?

> **leunam12 said:**
> Did you try avconv or winff (a frontend for avconv)?

I believe I tried avconv.

Video quality was poor with static.

Will look for winff.

---

### Post by &amp;KyT$0P# on 2016-07-18
> **4kh3RAm said:**
> How would I do that ?
Well, the output says this:
```
The encoder 'aac' is experimental but experimental codecs are not enabled, add '-strict -2' if you want to use it.
```
So, the command I posted is copy+paste of your command line and with -strict -2 added...

---

### Post by 4kh3RAm on 2016-07-18
Winff worked well.

Volume of video is very low even with vol set at max.

I think my Microsoft webcam has a crappy microphone.

I would like to find a webcam that has a decent microphone.

What good is a webcam if people have to read lips to understand what is being said. :-)

---

### Post by Yellow Pasque on 2016-07-19
Does the original have low volume? What exactly is winff converting to?
```
sudo apt-get install mediainfo
mediainfo convertedfile.mp4
```

---

### Post by 4kh3RAm on 2016-07-19
I had it convert to mp4.

I will be getting a better Logitech webcam in the future.

It has a better microphone.

---

