---
title: "Avconv; incompatible sample format"
date: 2014-06-16
forum: General Help
---

### Post by blnl on 2014-06-16
I need to convert my iPhone .mov to .avi.

Normally on my Fedora machine I use ffmpeg to manipulate the videos. I was surprised to see that ffmpeg does not work on Ubuntu:
```
boris@dc7100hp:~/Documents$ ffmpeg -i INPUT.mov -y -vf vflip,hflip -qscale 0 OUTPUT.avi
ffmpeg version 0.8.10-4:0.8.10-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Feb  6 2014 20:59:08 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.

Seems stream 0 codec frame rate differs from container frame rate: 1200.00 (1200/1) -> 29.97 (30000/1001)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'INPUT.mov':
  Metadata:
    major_brand     : qt  
    minor_version   : 0
    compatible_brands: qt  
    creation_time   : 2014-05-23 10:26:16
    encoder         : 7.1.1
    encoder-eng     : 7.1.1
    date            : 2014-05-23T12:26:16+0200
    date-eng        : 2014-05-23T12:26:16+0200
  Duration: 00:00:31.04, start: 0.000000, bitrate: 10738 kb/s
    Stream #0.0(und): Video: h264 (Baseline), yuv420p, 1280x720, 10669 kb/s, 29.97 fps, 29.97 tbr, 600 tbn, 1200 tbc
    Metadata:
      creation_time   : 2014-05-23 10:26:16
    Stream #0.1(und): Audio: aac, 44100 Hz, mono, s16, 63 kb/s
    Metadata:
      creation_time   : 2014-05-23 10:26:16
qscale must be > 0.0 and <= 255
Failed to set value '0' for option 'qscale'
```

So I decided to try avconv, as the ffmpeg program told me above. Surprisingly that did not work either:
```
boris@dc7100hp:~/Documents$ avconv -i INPUT.mov -y -vf vflip,hflip -qscale 0 OUTPUT.avi
avconv version 0.8.10-4:0.8.10-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Feb  6 2014 20:59:08 with gcc 4.6.3
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'INPUT.mov':
  Metadata:
    major_brand     : qt  
    minor_version   : 0
    compatible_brands: qt  
    creation_time   : 2014-05-23 10:26:16
    encoder         : 7.1.1
    encoder-eng     : 7.1.1
    date            : 2014-05-23T12:26:16+0200
    date-eng        : 2014-05-23T12:26:16+0200
  Duration: 00:00:31.04, start: 0.000000, bitrate: 10738 kb/s
    Stream #0.0(und): Video: h264 (Baseline), yuv420p, 1280x720, 10669 kb/s, 29.97 fps, 29.97 tbr, 600 tbn, 1200 tbc
    Metadata:
      creation_time   : 2014-05-23 10:26:16
    Stream #0.1(und): Audio: aac, 44100 Hz, mono, s16, 63 kb/s
    Metadata:
      creation_time   : 2014-05-23 10:26:16
[buffer @ 0x85041a0] w:1280 h:720 pixfmt:yuv420p
Incompatible sample format 's16' for codec 'ac3', auto-selecting format 'flt'
[ac3 @ 0x8506ae0] invalid bit rate
Output #0, avi, to 'OUTPUT.avi':
  Metadata:
    major_brand     : qt  
    minor_version   : 0
    compatible_brands: qt  
    creation_time   : 2014-05-23 10:26:16
    encoder         : 7.1.1
    encoder-eng     : 7.1.1
    date            : 2014-05-23T12:26:16+0200
    date-eng        : 2014-05-23T12:26:16+0200
    Stream #0.0(und): Video: mpeg4, yuv420p, 1280x720, q=2-31, 200 kb/s, 90k tbn, 29.97 tbc
    Metadata:
      creation_time   : 2014-05-23 10:26:16
    Stream #0.1(und): Audio: ac3, 44100 Hz, mono, flt, 200 kb/s
    Metadata:
      creation_time   : 2014-05-23 10:26:16
Stream mapping:
  Stream #0:0 -> #0:0 (h264 -> mpeg4)
  Stream #0:1 -> #0:1 (aac -> ac3)
Error while opening encoder for output stream #0:1 - maybe incorrect parameters such as bit_rate, rate, width or height
boris@dc7100hp:~/Documents$
```

What is it with "Incompatible sample format 's16' for codec 'ac3', auto-selecting format 'flt'"? How to resolve that?

I tried the solution suggested in [Thread: avconv error - Incompatible sample format s16 for codec ac3]("http://ubuntuforums.org/showthread.php?t=2002893&highlight=avconv%3B+incompatible+sample+format")
```
sudo apt-get install libavcodec-extra-53
```
It did not help, it still complains about "Incompatible sample format 's16' for codec 'ac3', auto-selecting format 'flt'"

Can someone please help me get this right in Ubuntu?
Am I missing some other codecs? How to install them?



By the way, there is nothing wrong with my input video. To prove that the video sample is not corrupted here is the ffmpeg output from my Fedora machine:
```
[boris@e6410dl Documents]$ ffmpeg -i INPUT.mov -y -vf vflip,hflip -qscale 0 OUTPUT.avi
ffmpeg version 2.1.4 Copyright (c) 2000-2014 the FFmpeg developers
  built on Feb 25 2014 08:24:47 with gcc 4.8.2 (GCC) 20131212 (Red Hat 4.8.2-7)
  configuration: --prefix=/usr --bindir=/usr/bin --datadir=/usr/share/ffmpeg --incdir=/usr/include/ffmpeg --libdir=/usr/lib64 --mandir=/usr/share/man --arch=x86_64 --optflags='-O2 -g -pipe -Wall -Wp,-D_FORTIFY_SOURCE=2 -fexceptions -fstack-protector-strong --param=ssp-buffer-size=4 -grecord-gcc-switches -m64 -mtune=generic' --enable-bzlib --disable-crystalhd --enable-frei0r --enable-gnutls --enable-libass --enable-libcdio --enable-libcelt --enable-libdc1394 --disable-indev=jack --enable-libfreetype --enable-libgsm --enable-libmp3lame --enable-openal --enable-libopencv --enable-libopenjpeg --enable-libopus --enable-libpulse --enable-libschroedinger --enable-libsoxr --enable-libspeex --enable-libtheora --enable-libvorbis --enable-libv4l2 --enable-libvpx --enable-libx264 --enable-libxvid --enable-x11grab --enable-avfilter --enable-avresample --enable-postproc --enable-pthreads --disable-static --enable-shared --enable-gpl --disable-debug --disable-stripping --shlibdir=/usr/lib64 --enable-runtime-cpudetect
  libavutil      52. 48.101 / 52. 48.101
  libavcodec     55. 39.101 / 55. 39.101
  libavformat    55. 19.104 / 55. 19.104
  libavdevice    55.  5.100 / 55.  5.100
  libavfilter     3. 90.100 /  3. 90.100
  libavresample   1.  1.  0 /  1.  1.  0
  libswscale      2.  5.101 /  2.  5.101
  libswresample   0. 17.104 /  0. 17.104
  libpostproc    52.  3.100 / 52.  3.100
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'INPUT.mov':
  Metadata:
    major_brand     : qt  
    minor_version   : 0
    compatible_brands: qt  
    creation_time   : 2014-05-23 10:26:16
    model           : iPhone 4
    model-eng       : iPhone 4
    encoder         : 7.1.1
    encoder-eng     : 7.1.1
    date            : 2014-05-23T12:26:16+0200
    date-eng        : 2014-05-23T12:26:16+0200
    location        : +43.5051+016.4520+044.314/
    location-eng    : +43.5051+016.4520+044.314/
    make            : Apple
    make-eng        : Apple
  Duration: 00:00:31.02, start: 0.000000, bitrate: 10746 kb/s
    Stream #0:0(und): Video: h264 (Baseline) (avc1 / 0x31637661), yuv420p(tv, bt709), 1280x720, 10669 kb/s, 29.97 fps, 29.97 tbr, 600 tbn, 1200 tbc (default)
    Metadata:
      creation_time   : 2014-05-23 10:26:16
      handler_name    : Core Media Data Handler
    Stream #0:1(und): Audio: aac (mp4a / 0x6134706D), 44100 Hz, mono, fltp, 63 kb/s (default)
    Metadata:
      creation_time   : 2014-05-23 10:26:16
      handler_name    : Core Media Data Handler
Please use -q:a or -q:v, -qscale is ambiguous
Output #0, avi, to 'OUTPUT.avi':
  Metadata:
    major_brand     : qt  
    minor_version   : 0
    compatible_brands: qt  
    make-eng        : Apple
    model           : iPhone 4
    model-eng       : iPhone 4
    make            : Apple
    encoder-eng     : 7.1.1
    ICRD            : 2014-05-23T12:26:16+0200
    date-eng        : 2014-05-23T12:26:16+0200
    location        : +43.5051+016.4520+044.314/
    location-eng    : +43.5051+016.4520+044.314/
    ISFT            : Lavf55.19.104
    Stream #0:0(und): Video: mpeg4 (FMP4 / 0x34504D46), yuv420p, 1280x720, q=2-31, 200 kb/s, 29.97 tbn, 29.97 tbc (default)
    Metadata:
      creation_time   : 2014-05-23 10:26:16
      handler_name    : Core Media Data Handler
    Stream #0:1(und): Audio: mp3 (libmp3lame) (U[0][0][0] / 0x0055), 44100 Hz, mono, fltp (default)
    Metadata:
      creation_time   : 2014-05-23 10:26:16
      handler_name    : Core Media Data Handler
Stream mapping:
  Stream #0:0 -> #0:0 (h264 -> mpeg4)
  Stream #0:1 -> #0:1 (aac -> libmp3lame)
Press [q] to stop, [?] for help
frame=  930 fps= 70 q=0.0 Lsize=  119263kB time=00:00:31.05 bitrate=31455.7kbits/s    
video:118959kB audio:243kB subtitle:0 global headers:0kB muxing overhead 0.051213%
[boris@e6410dl Documents]$
```

---

### Post by FakeOutdoorsman on 2014-06-17
The so-called "ffmpeg" in the repository (it was finally removed in 14.04) is a crappy counterfeit, and avconv is usually buggy, so I recommend trying the real ffmpeg. You can get a build at the [FFmpeg Download](http://ffmpeg.org/download.html#LinuxBuilds) page. Then just extract and run it (note the **./** before the ffmpeg):

```
./ffmpeg -y -i INPUT.mov -vf vflip,hflip -qscale 2 -metadata:s:v:0 rotate=0 OUTPUT.avi
```

Is there a particular reason you want AVI? It's a graybeard container and modern alternatives are generally a better choice.

---

### Post by blnl on 2014-06-17
So if I understood correctly, ffmpeg that you suggest is precompiled, it works out of the box.
I'll give it a try and see what happens.

I use AVI as an intermediate format, to get the right orientation, and sometimes I concatenate several AVI's together.
The end result is then resized to a progressive download video MPG and FLV for online viewing.

Thank you FakeOutdoorsman, it works perfectly.

I have copied it in the /usr/bin and overwritten the crappy Ubuntu ffmpeg. I hope this action will not destroy my system :confused:

---

### Post by FakeOutdoorsman on 2014-06-17
> **blnl said:**
> So if I understood correctly, ffmpeg that you suggest is precompiled, it works out of the box.
I'll give it a try and see what happens.
Yes, and often it works when the counterfeit does not.

> **blnl said:**
> I use AVI as an intermediate format, to get the right orientation
AVI is just a container format that can utilize many multimedia formats, but unfortunately in your case by default ffmpeg will use a lossy video format for AVI. I recommend using a lossless intermediate if you have a requirement to make an intermediate output file. Otherwise your're introducing an additional lossy conversion. Here are three examples you can experiment with.

```

ffmpeg -i input -vcodec huffyuv -acodec copy output.mkv
ffmpeg -i input -vcodec utvideo -acodec copy output.mkv
ffmpeg -i input -vcodec libx264 -qp 0 -preset veryfast -acodec copy output.mkv

```

> **blnl said:**
> and sometimes I concatenate several AVI's together
ffmpeg can concatenate some videos without the need to re-encode with the concat demuxer. See [How to concatenate (join, merge) media files](https://trac.ffmpeg.org/wiki/How%20to%20concatenate%20%28join,%20merge%29%20media%20files#demuxer).

Or you can rotate, concatenate, and prepare for web viewing all in one command:
```
ffmpeg -i input0 -i input1 -i input2 -filter_complex \
"[0:v]vflip,hflip,setpts=PTS-STARTPTS[v0]; \
 [1:v]vflip,hflip,setpts=PTS-STARTPTS[v1]; \
 [2:v]vflip,hflip,setpts=PTS-STARTPTS[v2]; \
 [v0][0:a][v1][1:a][v2][2:a]concat=n=3:v=1:a=1[v][a]" \
-map "[v]" -map "[a]" -vcodec libx264 -crf 23 -preset medium -movflags +faststart \
-c:a aac -strict experimental -b:a 192k output.mp4
```

[list]
[*]Since concat wants all inputs to start at timestamp 0 the setpts filter is added to do that.
[*]"-movflags +faststart" allows the video to begin playback before the file is completely downloaded.
[*]Other filters to rotate video include "transpose" and "rotate". See the [FFmpeg Filters Documentation](http://ffmpeg.org/ffmpeg-filters.html) on info on all filters.
[*]See [FFmpeg H.264 Encoding Guide](https://trac.ffmpeg.org/wiki/Encode/H.264) for more encoding info.
[*]If you're encoding for a bandwidth limited situation you should use VBV as shown in [Encoding for streaming sites](http://trac.ffmpeg.org/wiki/EncodingForStreamingSites).
[/list]

> **blnl said:**
> I have copied it in the /usr/bin and overwritten the crappy Ubuntu ffmpeg. I hope this action will not destroy my system :confused:
"/usr/bin/local" is safer (then you may have to run "hash ffmpeg" once).

Or you could avoid "the system" completely:
```
mkdir ~/bin
mv ffmpeg ~/bin
. ~/.profile
hash ffmpeg

```

Then just enter "ffmpeg" and it should use your new ffmpeg.

---

### Post by blnl on 2014-06-19
Thank you for the advice, I appreciate it.
Especial all in one example is interesting, I'll explore it to see if it suits my needs.

My approach is not so sophisticated. It is very pragmatic, but it does the job.
Yes, I know AVI is lossy, so I try to minimize the damage by "-qscale 0"
```

ffmpeg -i INPUT1.mov -y -qscale 0 OUTPUT1.avi
ffmpeg -i INPUT2.mov -y -vf transpose=1 -qscale 0 OUTPUT2.avi
ffmpeg -i INPUT3.mov -y -vf vflip,hflip -qscale 0 OUTPUT3.avi

cat OUTPUT1.avi OUTPUT2.avi OUTPUT3.avi > OUTPUT123.avi
ffmpeg -i OUTPUT123.avi -y -r 30 -qscale 0 OUTPUT.avi

```
That is what you get when you do not know how to use the tool efficiently :)
Well, there is certainly a lot more to learn here...

---

