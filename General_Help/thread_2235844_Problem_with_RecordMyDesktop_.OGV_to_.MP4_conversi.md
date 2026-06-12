---
title: "Problem with RecordMyDesktop .OGV to .MP4 conversion"
date: 2014-07-23
forum: General Help
---

### Post by jan26 on 2014-07-23
Hello everyone,

I am using Ubuntu 14.04 LTS and, to tell you the truth, I do not have much experience with Linux at all.

I am working with RecordMyDesktop program, that in my opinion is very good, but I have a problem when I want to edit my video.ogv using Kdenlive. I tried to convert my .ogv movies to mp4 with **avconv** and **mencoder**, but it did not work. I will show you couple of examples below, to make my situation more clear for you:

**AVCONV:**

Code:
```

avconv -i input.ogv output.mp4

```

Result:
```

avconv version 9.14-6:9.14-0ubuntu0.14.04.1, Copyright (c) 2000-2014 the Libav developers
  built on Jul 15 2014 13:57:40 with gcc 4.8 (Ubuntu 4.8.2-19ubuntu1)
[COLOR=#daa520][ogg @ 0x1fef020] Multiple fisbone for the same stream is not implemented. Update your Libav version to the newest one from Git. If the problem still occurs, it means that your file has a feature which has not been implemented.[/COLOR]
[ogg @ 0x1fef020] 22 bytes of comment header remain
[ogg @ 0x1fef020] truncated comment header, 1 comments not found
[COLOR=#daa520][ogg @ 0x1fef020] max_analyze_duration reached[/COLOR]
Input #0, ogg, from 'odcinek1-1.ogv':
  Duration: 00:01:39.06, start: 0.000000, bitrate: 998 kb/s
    Stream #0.0: Data: skeleton
    Stream #0.1: Video: theora, yuv420p, 1312x752 [PAR 1:1 DAR 82:47], 3.75 fps, 15 tbn, 15 tbc
    Stream #0.2: Audio: vorbis, 22050 Hz, mono, fltp, 66 kb/s
[libx264 @ 0x21d95c0] using SAR=1/1
[libx264 @ 0x21d95c0] using cpu capabilities: MMX2 SSE2Fast SSSE3 SSE4.2
[libx264 @ 0x21d95c0] profile High, level 3.2
[libx264 @ 0x21d95c0] 264 - core 142 r2389 956c8d8 - H.264/MPEG-4 AVC codec - Copyleft 2003-2014 - http://www.videolan.org/x264.html - options: cabac=1 ref=3 deblock=1:0:0 analyse=0x3:0x113 me=hex subme=7 psy=1 psy_rd=1.00:0.00 mixed_ref=1 me_range=16 chroma_me=1 trellis=1 8x8dct=1 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=-2 threads=12 lookahead_threads=2 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=3 b_pyramid=2 b_adapt=1 b_bias=0 direct=1 weightb=1 open_gop=0 weightp=2 keyint=250 keyint_min=3 scenecut=40 intra_refresh=0 rc_lookahead=40 rc=crf mbtree=1 crf=23.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 ip_ratio=1.25 aq=1:1.00
_[COLOR=#ff0000]encoder 'aac' is experimental and might produce bad results.[/COLOR]_
_[COLOR=#ff0000]Add '-strict experimental' if you want to use it.[/COLOR]_

```

Then I try something like this

Code:
```

avconv -i input.ogv -strict experimental output.mp4

```

Result:
```

avconv version 9.14-6:9.14-0ubuntu0.14.04.1, Copyright (c) 2000-2014 the Libav developers
  built on Jul 15 2014 13:57:40 with gcc 4.8 (Ubuntu 4.8.2-19ubuntu1)
[COLOR=#daa520][ogg @ 0x1c4c0e0] Multiple fisbone for the same stream is not implemented. Update your Libav version to the newest one from Git. If the problem still occurs, it means that your file has a feature which has not been implemented.[/COLOR]
[ogg @ 0x1c4c0e0] 22 bytes of comment header remain
[ogg @ 0x1c4c0e0] truncated comment header, 1 comments not found
[COLOR=#daa520][ogg @ 0x1c4c0e0] max_analyze_duration reached[/COLOR]
Input #0, ogg, from 'odcinek1-1.ogv':
  Duration: 00:01:39.06, start: 0.000000, bitrate: 998 kb/s
    Stream #0.0: Data: skeleton
    Stream #0.1: Video: theora, yuv420p, 1312x752 [PAR 1:1 DAR 82:47], 3.75 fps, 15 tbn, 15 tbc
    Stream #0.2: Audio: vorbis, 22050 Hz, mono, fltp, 66 kb/s
File 'odcinek1-1.mp4' already exists. Overwrite ? [y/N] y
[libx264 @ 0x1e36080] using SAR=1/1
[libx264 @ 0x1e36080] using cpu capabilities: MMX2 SSE2Fast SSSE3 SSE4.2
[libx264 @ 0x1e36080] profile High, level 3.2
[libx264 @ 0x1e36080] 264 - core 142 r2389 956c8d8 - H.264/MPEG-4 AVC codec - Copyleft 2003-2014 - http://www.videolan.org/x264.html - options: cabac=1 ref=3 deblock=1:0:0 analyse=0x3:0x113 me=hex subme=7 psy=1 psy_rd=1.00:0.00 mixed_ref=1 me_range=16 chroma_me=1 trellis=1 8x8dct=1 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=-2 threads=12 lookahead_threads=2 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=3 b_pyramid=2 b_adapt=1 b_bias=0 direct=1 weightb=1 open_gop=0 weightp=2 keyint=250 keyint_min=3 scenecut=40 intra_refresh=0 rc_lookahead=40 rc=crf mbtree=1 crf=23.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 ip_ratio=1.25 aq=1:1.00
_[COLOR=#ff0000][aac @ 0x1e364c0] Too many bits per frame requested[/COLOR]_
Output #0, mp4, to 'odcinek1-1.mp4':
    Stream #0.0: Video: libx264, yuv420p, 1312x752 [PAR 1:1 DAR 82:47], q=-1--1, 90k tbn, 3.75 tbc
    Stream #0.1: Audio: aac, 22050 Hz, mono, fltp, 200 kb/s
Stream mapping:
  Stream #0:1 -> #0:0 (theora -> libx264)
  Stream #0:2 -> #0:1 (vorbis -> aac)
_[COLOR=#ff0000]Error while opening encoder for output stream #0:1 - maybe incorrect parameters such as bit_rate, rate, width or height[/COLOR]_

```


**MENCODER:**

Code:
```

mencoder input.ogv -of lavf -lavfopts format=mp4 -oac mp3lame -lameopts cbr:br=128 -ovc x264 -x264encopts bitrate=1000 -o output.mp4

```

Result:
```

opts bitrate=1000 -o final.mp4
MEncoder 1.1-4.8 (C) 2000-2012 MPlayer Team
success: format: 0  data: 0x0 - 0x29bd52c
libavformat version 54.20.4 (external)
Mismatching header version 54.20.3
libavformat file format detected.
[ogg @ 0x7f5681eb4600]Multiple fisbone for the same stream is not implemented. Update your Libav version to the newest one from Git. If the problem still occurs, it means that your file has a feature which has not been implemented.
[ogg @ 0x7f5681eb4600]22 bytes of comment header remain
[ogg @ 0x7f5681eb4600]truncated comment header, 1 comments not found
[ogg @ 0x7f5681eb4600]max_analyze_duration reached
[lavf] stream 1: video (theora), -vid 0
[lavf] stream 2: audio (vorbis), -aid 0
VIDEO:  [theo]  1312x752  0bpp   -nan fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:44  fourcc:0x6F656874  size:1312x752  fps: -nan  ftime:=  -nan
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
libavcodec version 54.35.0 (external)
AUDIO: 22050 Hz, 1 ch, floatle, 66.0 kbit/9.35% (ratio: 8250->88200)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis)
==========================================================================
** MUXER_LAVF *****************************************************************
REMEMBER: MEncoder's libavformat muxing is presently broken and can generate
INCORRECT files in the presence of B-frames. Moreover, due to bugs MPlayer
will play these INCORRECT files as if nothing were wrong!
*******************************************************************************
OK, exit.
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [fftheora] vfm: ffmpeg (FFmpeg Theora)
==========================================================================
MP3 audio selected.
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
Movie-Aspect is 1.74:1 - prescaling to correct movie aspect.
[swscaler @ 0x7f568210a640]using unscaled yuv420p -> yuv420p special converter
x264 [info]: using SAR=1/1
x264 [info]: using cpu capabilities: MMX2 SSE2Fast SSSE3 SSE4.2
x264 [info]: profile High, level 3.2
Pos:  -nans      2f ( 1%)  0.00fps Trem:   0min   0mb  A-V: -nan [0:0]
[VD_FFMPEG] DRI failure.
Pos:  -nans    716f (20%) 85.16fps Trem:   0min   0mb  A-V: -nan [0:0]]


Too many audio packets in the buffer: (4096 in 643996 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
Pos:  -nans    717f (20%) 85.23fps Trem:   0min   0mb  A-V: -nan [0:0]


Too many audio packets in the buffer: (4096 in 643996 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
Pos:  -nans    718f (20%) 85.34fps Trem:   0min   0mb  A-V: -nan [0:0]


Flushing video frames.
VIDEO CODEC ID: 28
AUDIO CODEC ID: 15001, TAG: 0
Writing header...
[mp4 @ 0x7f5681eb4600]time base not set
[COLOR=#ff0000]B&#322;&#261;d w obliczeniach zmiennoprzecinkowych (core dumped)[/COLOR]

```

The [COLOR=#ff0000]red[/COLOR][COLOR=#ff0000] highlighted[/COLOR] phrase means: "Error in floating-point calculations"

Conversion to .AVI works, but final quality is low.

Please help me.

---

### Post by FakeOutdoorsman on 2014-07-24
avconv is buggy. Get a static ffmpeg build via the [FFmpeg Download](http://ffmpeg.org/download.html) page, or just do this:

```
wget http://ffmpeg.gusari.org/static/32bit/ffmpeg.static.32bit.latest.tar.gz
tar xzvf ffmpeg.static.32bit.latest.tar.gz
```

Then run it (notice the **./**). If you're going to edit this in Kdenlive (I'm guessing Kdenlive doesn't like input.ogv), then use a lossless format so you can minimize the number of lossy encodings and it will also probably be more editor friendly:

```
./ffmpeg -i input.ogv -c:v huffyuv -c:a pcm_s16le output.mkv
```

Import output.mkv into your editor, do your editing, and then output from your editor to MP4.

---

### Post by grumblebum2 on 2014-07-24
**@ jan26 **
You may want to look at [**_[COLOR="#B22222"]SimpleScreenRecorder[/COLOR]_**]("http://www.maartenbaert.be/simplescreenrecorder/")
You can install from an ubuntu ppa.

Record directly to mp4. Also allows pause/resume of recording.
You can monitor the elapsed time and recording file size.
See the attached file. mp4 23secs_ 368kB

---

### Post by jan26 on 2014-07-24
**@FakeOutdoorsman**

For me it did not work:

Code:
```

./ffmpeg -i odcinek1.ogv -c:v huffyuv -c:v pcm_s16le output.mkv

```

Result:
```

ffmpeg version N-63893-gc69defd Copyright (c) 2000-2014 the FFmpeg developers
  built on Jul 16 2014 05:13:25 with gcc 4.6 (Debian 4.6.3-1)
  configuration: --prefix=/root/ffmpeg-static/32bit --arch=x86_32 --extra-cflags='-m32 -I/root/ffmpeg-static/32bit/include -static' --extra-ldflags='-m32 -L/root/ffmpeg-static/32bit/lib -static' --extra-libs='-lxml2 -lexpat -lfreetype' --enable-static --disable-shared --disable-ffserver --disable-doc --enable-bzlib --enable-zlib --enable-postproc --enable-runtime-cpudetect --enable-libx264 --enable-gpl --enable-libtheora --enable-libvorbis --enable-libmp3lame --enable-gray --enable-libass --enable-libfreetype --enable-libopenjpeg --enable-libspeex --enable-libvo-aacenc --enable-libvo-amrwbenc --enable-version3 --enable-libvpx
  libavutil      52. 89.100 / 52. 89.100
  libavcodec     55. 66.101 / 55. 66.101
  libavformat    55. 43.100 / 55. 43.100
  libavdevice    55. 13.101 / 55. 13.101
  libavfilter     4.  8.100 /  4.  8.100
  libswscale      2.  6.100 /  2.  6.100
  libswresample   0. 19.100 /  0. 19.100
  libpostproc    52.  3.100 / 52.  3.100
[COLOR=#800080][ogg @ 0x9d7ae40][/COLOR] [COLOR=#daa520]Broken file, keyframe not correctly marked.[/COLOR]
Input #0, ogg, from 'odcinek1.ogv':
  Duration: 00:07:16.93, start: 0.000000, bitrate: 801 kb/s
    Stream #0:0: Data: none
    Stream #0:1: Video: theora, yuv420p, 1312x752 [SAR 1:1 DAR 82:47], 15 fps, 15 tbr, 15 tbn, 15 tbc
    Metadata:
      RECORDMYDESKTOP : 0.3.8.1
    Stream #0:2: Audio: vorbis, 22050 Hz, mono, fltp, 66 kb/s
[COLOR=#ff0000]_Invalid encoder type 'pcm_s16le'_[/COLOR]


```



[B]@grumblebum2

[/B]It works very well :p


Thank you very much guys.

---

### Post by FakeOutdoorsman on 2014-07-24
Sorry, that was a typo in my example. I fixed it.

---

