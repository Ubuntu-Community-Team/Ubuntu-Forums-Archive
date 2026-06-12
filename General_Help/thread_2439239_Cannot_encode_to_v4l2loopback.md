---
title: "Cannot encode to v4l2loopback"
date: 2020-03-24
forum: General Help
---

### Post by d2105284 on 2020-03-24
I installed v4l2loopback using [these instructions]("https://superuser.com/a/1331422") to build from source.  However I can't get ffmpeg to encode:

```
$ v4l2-ctl --list-devicesDummy video device (0x0000) (platform:v4l2loopback-000):
    /dev/video2


Integrated Camera: Integrated C (usb-0000:00:14.0-8):
    /dev/video0
    /dev/video1


$ ffmpeg -re -i video.mp4 -f v4l2 /dev/video2
ffmpeg version 3.4.6-0ubuntu0.18.04.1 Copyright (c) 2000-2019 the FFmpeg developers
  built with gcc 7 (Ubuntu 7.3.0-16ubuntu3)
  configuration: --prefix=/usr --extra-version=0ubuntu0.18.04.1 --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --enable-gpl --disable-stripping --enable-avresample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librubberband --enable-librsvg --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzmq --enable-libzvbi --enable-omx --enable-openal --enable-opengl --enable-sdl2 --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libopencv --enable-libx264 --enable-shared
  libavutil      55. 78.100 / 55. 78.100
  libavcodec     57.107.100 / 57.107.100
  libavformat    57. 83.100 / 57. 83.100
  libavdevice    57. 10.100 / 57. 10.100
  libavfilter     6.107.100 /  6.107.100
  libavresample   3.  7.  0 /  3.  7.  0
  libswscale      4.  8.100 /  4.  8.100
  libswresample   2.  9.100 /  2.  9.100
  libpostproc    54.  7.100 / 54.  7.100
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'video.mp4':
  Metadata:
    major_brand     : dash
    minor_version   : 0
    compatible_brands: iso6avc1mp41
    creation_time   : 2020-01-19T16:58:03.000000Z
  Duration: 00:03:32.04, start: 0.000000, bitrate: 661 kb/s
    Stream #0:0(und): Video: h264 (Main) (avc1 / 0x31637661), yuv420p(tv, bt709, progressive), 1280x720 [SAR 1:1 DAR 16:9], 11 kb/s, 25 fps, 25 tbr, 12800 tbn, 50 tbc (default)
    Metadata:
      creation_time   : 2020-01-19T16:58:03.000000Z
      handler_name    : ISO Media file produced by Google Inc.
Stream mapping:
  Stream #0:0 -> #0:0 (h264 (native) -> rawvideo (native))
Press [q] to stop, [?] for help
[v4l2 @ 0x55f83cd2e100] ioctl(VIDIOC_G_FMT): Invalid argument
Could not write header for output file #0 (incorrect codec parameters ?): Invalid argument
Error initializing output stream 0:0 -- 
Conversion failed!
```

---

### Post by HermanAB on 2020-03-25
I don't know why you want to use a loopback device, but you probably don't need it.

A video stream is bidirectional - the client needs to talk to the server.  A lot actually happens in the background to make pause and fast forward etc. possible. These video control protocols are RTP and RTSP.

Therefore the better way to handle video streams is to set up a multicasting streaming server on the device using ffmpeg and then you can have as many subscribers as you want. If your source is unicast and cannot be changed, then you can restream it with ffmpeg to multicast.

In other words, try to handle your problem at the ethernet level and not at the device level.

Maybe you should read these: 
[https://www.aeronetworks.ca/2018/04/raspberry-pi-video-streaming.html](https://www.aeronetworks.ca/2018/04/raspberry-pi-video-streaming.html)
[https://www.aeronetworks.ca/2018/05/mpeg-2-transport-streams.html](https://www.aeronetworks.ca/2018/05/mpeg-2-transport-streams.html)

---

### Post by d2105284 on 2020-03-25
This isn't a video server.  I'm creating a video device for applications that expect a stream e.g. web conferencing.

---

### Post by HermanAB on 2020-03-25
So then it is a video video client.  FFMPEG and Gstreamer can do both server and client functions.

---

### Post by d2105284 on 2020-03-25
Regardless, that solution is overkill for what I need

---

### Post by HermanAB on 2020-03-26
Hmm, but blowing against the wind won't get you anywhere either...

You should be able to create a device node using tee and socat, but grokking the socat manual is not easy.

---

