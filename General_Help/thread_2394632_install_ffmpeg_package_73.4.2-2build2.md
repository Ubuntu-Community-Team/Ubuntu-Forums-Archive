---
title: "install ffmpeg package 7:3.4.2-2build2"
date: 2018-06-19
forum: General Help
---

### Post by mojtaba472 on 2018-06-19
hello
how install ffmpeg package 7:3.4.2-2build2 ?
Link 7:3.4.2-2build2 : [https://launchpad.net/ubuntu/+source/ffmpeg](https://launchpad.net/ubuntu/+source/ffmpeg)
Help me
and ffmpeg install package in : [https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu](https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu)

When I convert a movie to the following error message, how should I fix it?
error:
> 

```


**Command:** ffmpeg -i test.avi -vcodec libx264 -s 640x360 -threads 4 -movflags faststart test.mp4


ffmpeg version 2.8.14-0ubuntu0.16.04.1 Copyright (c) 2000-2018 the FFmpeg developers
  built with gcc 5.4.0 (Ubuntu 5.4.0-6ubuntu1~16.04.9) 20160609
  configuration: --prefix=/usr --extra-version=0ubuntu0.16.04.1 --build-suffix=-ffmpeg --toolchain=hardened --libdir=/usr/lib/i386-linux-gnu --incdir=/usr/include/i386-linux-gnu --cc=cc --cxx=g++ --enable-gpl --enable-shared --disable-stripping --disable-decoder=libopenjpeg --disable-decoder=libschroedinger --enable-avresample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmodplug --enable-libmp3lame --enable-libopenjpeg --enable-libopus --enable-libpulse --enable-librtmp --enable-libschroedinger --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxvid --enable-libzvbi --enable-openal --enable-opengl --enable-x11grab --enable-libdc1394 --enable-libiec61883 --enable-libzmq --enable-frei0r --enable-libx264 --enable-libopencv --disable-i686
  libavutil      54. 31.100 / 54. 31.100
  libavcodec     56. 60.100 / 56. 60.100
  libavformat    56. 40.101 / 56. 40.101
  libavdevice    56.  4.100 / 56.  4.100
  libavfilter     5. 40.101 /  5. 40.101
  libavresample   2.  1.  0 /  2.  1.  0
  libswscale      3.  1.101 /  3.  1.101
  libswresample   1.  2.101 /  1.  2.101
  libpostproc    53.  3.100 / 53.  3.100
Input #0, avi, from 'test.avi':
  Metadata:
    encoder         : MEncoder 2:1.0~rc2-0ubuntu13
  Duration: 00:09:56.46, start: 0.000000, bitrate: 2099 kb/s
    Stream #0:0: Video: msmpeg4v2 (MP42 / 0x3234504D), yuv420p, 854x480, 1840 kb/s, 24 fps, 24 tbr, 24 tbn, 24 tbc
    Stream #0:1: Audio: mp3 (U[0][0][0] / 0x0055), 48000 Hz, stereo, s16p, 245 kb/s
[libx264 @ 0x9298700] using cpu capabilities: MMX2 SSE2Fast SSSE3 SSE4.2 AVX
[libx264 @ 0x9298700] profile High, level 3.0
[libx264 @ 0x9298700] 264 - core 148 r2643 5c65704 - H.264/MPEG-4 AVC codec - Copyleft 2003-2015 - http://www.videolan.org/x264.html - options: cabac=1 ref=3 deblock=1:0:0 analyse=0x3:0x113 me=hex subme=7 psy=1 psy_rd=1.00:0.00 mixed_ref=1 me_range=16 chroma_me=1 trellis=1 8x8dct=1 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=-2 threads=4 lookahead_threads=1 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=3 b_pyramid=2 b_adapt=1 b_bias=0 direct=1 weightb=1 open_gop=0 weightp=2 keyint=250 keyint_min=24 scenecut=40 intra_refresh=0 rc_lookahead=40 rc=crf mbtree=1 crf=23.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 ip_ratio=1.40 aq=1:1.00
[aac @ 0x9299820] **The encoder 'aac' is experimental but experimental codecs are not enabled, add '-strict -2' if you want to use it.**




```



tnx

---

### Post by #&amp;thj^% on 2018-06-19
I have no solution for you but you might get more help posting in a support area rather than tutorials. :)
You can ask a staff member to move your thread to a better suited area by selecting "Report Post" in the bottom left corner of your original post.
Good Luck

---

### Post by Frogs Hair on 2018-06-19
Moved to *General Help*.

---

### Post by nlee2 on 2018-06-19
Have you tried

ffmpeg -i test.avi **-strict -2 **-vcodec libx264 -s 640x360 -threads 4 -movflags faststart test.mp4

---

