---
title: "Hardware encoding a webcam stream to Youtube on Raspberry Pi 4B"
date: 2020-05-06
forum: General Help
---

### Post by mfreeborn on 2020-05-06
Hi all,


 I've been going round in circles for a couple of weeks on this now.


I'm running 64-bit Ubuntu 19.10 on a Raspberry Pi 4B 4GB with Gnome desktop as a server. I have a couple of Rapsberry Pi Zero-based cameras running [RPi Cam Web Interface]("https://elinux.org/RPi-Cam-Web-Interface") which streams Motion JPEG on my local network. The goal is for the the RPi 4B server to take in these streams and beam them up to Youtube, which I can do without much problem using software H264 encoding with ffmpeg.


The issue is that using software encoding is obviously very CPU intensive - I would like to do the heavy lifting in hardware.


With the differences between older RPis and the RPi 4B, as well as using Ubuntu vs Raspbian and 64-bit vs 32-bit, I just haven;t been able to get my head around how to make this all work with hardware encoding.


The closest I can get is by running this command (on a random .gif from the internet):


```
ffmpeg -i test.gif -c:v h264_omx test.mp4 -y
```


Which produces the following output:


```
pi@pi4:~$ ffmpeg -i test.gif -c:v h264_omx test.mp4 -y
ffmpeg version 4.1.4-1build2 Copyright (c) 2000-2019 the FFmpeg developers
  built with gcc 9 (Ubuntu 9.2.1-4ubuntu1)
  configuration: --prefix=/usr --extra-version=1build2 --toolchain=hardened --libdir=/usr/lib/aarch64-linux-gnu --incdir=/usr/include/aarch64-linux-gnu --arch=arm64 --enable-gpl --disable-stripping --enable-avresample --disable-filter=resample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libaom --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libcodec2 --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libjack --enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librsvg --enable-librubberband --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvidstab --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzmq --enable-libzvbi --enable-lv2 --enable-omx --enable-openal --enable-opengl --enable-sdl2 --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libx264 --enable-shared
  libavutil      56. 22.100 / 56. 22.100
  libavcodec     58. 35.100 / 58. 35.100
  libavformat    58. 20.100 / 58. 20.100
  libavdevice    58.  5.100 / 58.  5.100
  libavfilter     7. 40.101 /  7. 40.101
  libavresample   4.  0.  0 /  4.  0.  0
  libswscale      5.  3.100 /  5.  3.100
  libswresample   3.  3.100 /  3.  3.100
  libpostproc    55.  3.100 / 55.  3.100
Input #0, gif, from 'test.gif':
  Duration: N/A, bitrate: N/A
    Stream #0:0: Video: gif, bgra, 500x375, 14.25 fps, 28.58 tbr, 100 tbn, 100 tbc
Stream mapping:
  Stream #0:0 -> #0:0 (gif (native) -> h264 (h264_omx))
Press [q] to stop, [?] for help
[h264_omx @ 0xaaaacb5fe4a0] libOMX_Core.so not found
[h264_omx @ 0xaaaacb5fe4a0] libOmxCore.so not found
Error initializing output stream 0:0 -- Error while opening encoder for output stream #0:0 - maybe incorrect parameters such as bit_rate, rate, width or height
Conversion failed!
```


Or, if I use the encoder "h264_v4l2m2m", I get:


```
pi@pi4:~$ ffmpeg -i test.gif -c:v h264_v4l2m2m test.mp4 -y
ffmpeg version 4.1.4-1build2 Copyright (c) 2000-2019 the FFmpeg developers
  built with gcc 9 (Ubuntu 9.2.1-4ubuntu1)
  configuration: --prefix=/usr --extra-version=1build2 --toolchain=hardened --libdir=/usr/lib/aarch64-linux-gnu --incdir=/usr/include/aarch64-linux-gnu --arch=arm64 --enable-gpl --disable-stripping --enable-avresample --disable-filter=resample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libaom --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libcodec2 --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libjack --enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librsvg --enable-librubberband --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvidstab --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzmq --enable-libzvbi --enable-lv2 --enable-omx --enable-openal --enable-opengl --enable-sdl2 --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libx264 --enable-shared
  libavutil      56. 22.100 / 56. 22.100
  libavcodec     58. 35.100 / 58. 35.100
  libavformat    58. 20.100 / 58. 20.100
  libavdevice    58.  5.100 / 58.  5.100
  libavfilter     7. 40.101 /  7. 40.101
  libavresample   4.  0.  0 /  4.  0.  0
  libswscale      5.  3.100 /  5.  3.100
  libswresample   3.  3.100 /  3.  3.100
  libpostproc    55.  3.100 / 55.  3.100
Input #0, gif, from 'test.gif':
  Duration: N/A, bitrate: N/A
    Stream #0:0: Video: gif, bgra, 500x375, 14.25 fps, 28.58 tbr, 100 tbn, 100 tbc
Stream mapping:
  Stream #0:0 -> #0:0 (gif (native) -> h264 (h264_v4l2m2m))
Press [q] to stop, [?] for help
[h264_v4l2m2m @ 0xaaaafe6264a0] Could not find a valid device
[h264_v4l2m2m @ 0xaaaafe6264a0] can't configure encoder
Error initializing output stream 0:0 -- Error while opening encoder for output stream #0:0 - maybe incorrect parameters such as bit_rate, rate, width or height
Conversion failed!
```


Anyone got any pointers?

---

### Post by HermanAB on 2020-05-06
Well, what hardware do you want to do the encoding on?  The only processor you have on a RPi is the CPU.

---

### Post by mfreeborn on 2020-05-06
The Raspberry Pi does have hardware blocks for some video encoding and decoding: [https://www.raspberrypi.org/products/raspberry-pi-4-model-b/specifications/](https://www.raspberrypi.org/products/raspberry-pi-4-model-b/specifications/)

I've also been able to get this to work on the standard Raspbian OS out of the box. (AN easy answer would be to say "Just use Raspbian, then", but I would really like to be able to run Ubuntu on the Raspberry Pi, and this should be technically do-able.

---

### Post by HermanAB on 2020-05-06
OK, but it is limited to certain specific resolutions - it is not a GPU:
H.265 (4kp60 decode), H264 (1080p60 decode, 1080p30 encode)

You need to recompile ffmpeg or gstreamer to make it work:
[https://stackoverflow.com/questions/60529213/how-to-enable-hardware-support-for-h-264-encoding-on-raspberry-pi-4b](https://stackoverflow.com/questions/60529213/how-to-enable-hardware-support-for-h-264-encoding-on-raspberry-pi-4b) 

I have recompiled those two in the past, but it was very painful to get all the required libraries and other dependencies resolved:
[https://www.aeronetworks.ca/2015/11/compile-latest-ffplay-from-source.html?m=1](https://www.aeronetworks.ca/2015/11/compile-latest-ffplay-from-source.html?m=1)
[https://www.aeronetworks.ca/2018/06/compile-latest-gstreamer-from-git.html](https://www.aeronetworks.ca/2018/06/compile-latest-gstreamer-from-git.html)

---

