---
title: "FFMPEG returns an error while trying to screencapture using AMD VCE"
date: 2017-12-10
forum: General Help
---

### Post by johnstefnds on 2017-12-10
I want to record my screen when playing games using my GPU's VCE because OBS and other similar software encoder screen capture software just take a big hit on my avg fps.

The issue is that why I try to do that with FFMPEG like this:

```
ffmpeg -vaapi_device /dev/dri/renderD128 -f x11grab -video_size 1920x1080 -i :0 -vf 'hwupload,scale_vaapi=format=nv12' -c:v h264_vaapi -qp 24 output.mp4
```

I get this output with an error at the end of it

```
ffmpeg version 3.3.4-2 Copyright (c) 2000-2017 the FFmpeg developers
  built with gcc 7 (Ubuntu 7.2.0-8ubuntu2)
  configuration: --prefix=/usr --extra-version=2 --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --enable-gpl --disable-stripping --enable-avresample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmp3lame --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librubberband --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxvid --enable-libzmq --enable-libzvbi --enable-omx --enable-openal --enable-opengl --enable-sdl2 --enable-libdc1394 --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libopencv --enable-libx264 --enable-shared
  WARNING: library configuration mismatch
  avcodec     configuration: --prefix=/usr --extra-version=2 --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --enable-gpl --disable-stripping --enable-avresample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmp3lame --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librubberband --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxvid --enable-libzmq --enable-libzvbi --enable-omx --enable-openal --enable-opengl --enable-sdl2 --enable-libdc1394 --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libopencv --enable-libx264 --enable-shared --enable-version3 --disable-doc --disable-programs --enable-libopencore_amrnb --enable-libopencore_amrwb --enable-libtesseract --enable-libvo_amrwbenc --enable-netcdf
  libavutil      55. 58.100 / 55. 58.100
  libavcodec     57. 89.100 / 57. 89.100
  libavformat    57. 71.100 / 57. 71.100
  libavdevice    57.  6.100 / 57.  6.100
  libavfilter     6. 82.100 /  6. 82.100
  libavresample   3.  5.  0 /  3.  5.  0
  libswscale      4.  6.100 /  4.  6.100
  libswresample   2.  7.100 /  2.  7.100
  libpostproc    54.  5.100 / 54.  5.100
libva info: VA-API version 0.40.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/radeonsi_drv_video.so
libva info: Found init function __vaDriverInit_0_40
libva info: va_openDriver() returns 0
[COLOR=#800080][x11grab @ 0x56274889c1c0][/COLOR][COLOR=#ffd700] [/COLOR][COLOR=#daa520]Stream #0: not enough frames to estimate rate; consider increasing probesize[/COLOR][COLOR=#ffff00]
[/COLOR]Input #0, x11grab, from ':0':   _______________________________________                                                                                                                                          
  Duration: N/A, start: 1512886283.032477, bitrate: N/A
    Stream #0:0: Video: rawvideo (BGR[0] / 0x524742), bgr0, 1920x1080, 29.97 fps, 1000k tbr, 1000k tbn, 1000k tbc
Stream mapping:
  Stream #0:0 -> #0:0 (rawvideo (native) -> h264 (h264_vaapi))
Press [q] to stop, [?] for help
[COLOR=#008080][h264_vaapi @ 0x5627488a8e80][/COLOR] [COLOR=#ff0000]B frames are not supported (0x1).
Error initializing output stream 0:0 -- Error while opening encoder for output stream #0:0 - maybe incorrect parameters such as bit_rate, rate, width or height
Conversion failed![/COLOR]

```


Any ideas on how to fix it? Is there a way to turn those B frames off? (whatever they are..I am not really sure all I know is that they are a kind of frame in a sequence or something :P ) 


I use the latest 4.15 kernel ubuntu 17.10 MESA 17.7dev LLVM6 xorg gnome 3.26 my cpu is AMD FX 8320 (with the propriatery driver) and my GPU RX 580

---

### Post by Yellow Pasque on 2017-12-10
Maybe use "-bf 0" or "-profile main" ???

---

### Post by mc4man on 2017-12-10
> **Temüjin said:**
> Maybe use "-bf 0" or "-profile main" ???
Maybe -profile:v 66  instead of main..
(- and if need be use both the -bf & -profile parameters.

---

### Post by Yellow Pasque on 2017-12-10
> **mc4man said:**
> Maybe -profile:v 66  instead of main..

I thought it was already defaulting to baseline profile, which doesn't support B frames, and causing the error?

---

### Post by mc4man on 2017-12-10
> **Temüjin said:**
> I thought it was already defaulting to baseline profile, which doesn't support B frames, and causing the error?
Here, (haswell) baseline isn't available. The orig command works, as does both -bf 0 and or  -profile:v 66.
The orig. uses 'high', -bf 0 uses 'high' -profile:v 66 uses constrained baseline, e.g
> [h264_vaapi @ 0x55bfaa39cb40] H.264 baseline profile is not supported, using constrained baseline profile instead.



---

### Post by johnstefnds on 2017-12-10
First off, thank you for posting. 
[COLOR=#a9a9a9]
But could you guys talk to me like I am not on the same level as you are? you are telling me to put some parameters as if I know my way around FFMPEG which probably is not the case.. for example **WHERE** to put -bf 0? next to -vf?  should I delete -vf and put -bf instead? how to proper indicate the "0" part like -bf=0 ? because if I put (next to -vf) -bf 0 just with a simple space I get the same output as in OP but this time with  the error:  "Unable to find a suitable output format for '0'
0: Invalid argument"

Same goes with the "-profile main" parameter... I tried to put it next to -vf and I got "Unable to find a suitable output format for 'main'
main: Invalid argument"

Then I tried to put it next to " -vaapi_device" and I got "[AVHWDeviceContext @ 0x562c8f001c00] No VA display found for device: -profile.
[vaapi @ 0x562c8e86c050] Failed to create a VAAPI device"[/COLOR]

Thank you.

---

### Post by johnstefnds on 2017-12-10
Ok when I type the command including -bf 0 like this

```
ffmpeg -vaapi_device /dev/dri/renderD128 -f x11grab -video_size 1920x1080 -i :0 -bf 0 -vf 'hwupload,scale_vaapi=format=nv12' -c:v h264_vaapi -qp 24 test.mp4
```

It shows activity in terminal like this: 
```


ffmpeg version 3.3.4-2 Copyright (c) 2000-2017 the FFmpeg developers
  built with gcc 7 (Ubuntu 7.2.0-8ubuntu2)
  configuration: --prefix=/usr --extra-version=2 --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --enable-gpl --disable-stripping --enable-avresample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmp3lame --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librubberband --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxvid --enable-libzmq --enable-libzvbi --enable-omx --enable-openal --enable-opengl --enable-sdl2 --enable-libdc1394 --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libopencv --enable-libx264 --enable-shared
  WARNING: library configuration mismatch
  avcodec     configuration: --prefix=/usr --extra-version=2 --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --enable-gpl --disable-stripping --enable-avresample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmp3lame --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librubberband --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxvid --enable-libzmq --enable-libzvbi --enable-omx --enable-openal --enable-opengl --enable-sdl2 --enable-libdc1394 --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libopencv --enable-libx264 --enable-shared --enable-version3 --disable-doc --disable-programs --enable-libopencore_amrnb --enable-libopencore_amrwb --enable-libtesseract --enable-libvo_amrwbenc --enable-netcdf
  libavutil      55. 58.100 / 55. 58.100
  libavcodec     57. 89.100 / 57. 89.100
  libavformat    57. 71.100 / 57. 71.100
  libavdevice    57.  6.100 / 57.  6.100
  libavfilter     6. 82.100 /  6. 82.100
  libavresample   3.  5.  0 /  3.  5.  0
  libswscale      4.  6.100 /  4.  6.100
  libswresample   2.  7.100 /  2.  7.100
  libpostproc    54.  5.100 / 54.  5.100
libva info: VA-API version 0.40.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/radeonsi_drv_video.so
libva info: Found init function __vaDriverInit_0_40
libva info: va_openDriver() returns 0
[x11grab @ 0x564e4bc57240] Stream #0: not enough frames to estimate rate; consider increasing probesize
Input #0, x11grab, from ':0':
  Duration: N/A, start: 1512960823.581819, bitrate: N/A
    Stream #0:0: Video: rawvideo (BGR[0] / 0x524742), bgr0, 1920x1080, 29.97 fps, 1000k tbr, 1000k tbn, 1000k tbc
Stream mapping:
  Stream #0:0 -> #0:0 (rawvideo (native) -> h264 (h264_vaapi))
Press [q] to stop, [?] for help
[h264_vaapi @ 0x564e4bc63f00] Warning: some packed headers are not supported (want 0xd, got 0).
Output #0, mp4, to 'test.mp4':
  Metadata:
    encoder         : Lavf57.71.100
    Stream #0:0: Video: h264 (h264_vaapi) (High) ([33][0][0][0] / 0x0021), vaapi_vld, 1920x1080, q=0-31, 29.97 fps, 30k tbn, 29.97 tbc
    Metadata:
      encoder         : Lavc57.89.100 h264_vaapi
frame=   18 fps=0.0 q=-0.0 size=     165kB time=00:00:00.56 bitrate=2383.9kbits/Past duration 0.623070 too large
Past duration 0.837120 too large
Past duration 0.910789 too large
frame=   35 fps= 34 q=-0.0 size=     185kB time=00:00:01.13 bitrate=1337.1kbits/frame=   51 fps= 32 q=-0.0 size=     197kB time=00:00:01.66 bitrate= 968.7kbits/frame=   67 fps= 32 q=-0.0 size=     205kB time=00:00:02.20 bitrate= 761.7kbits/frame=   82 fps= 31 q=-0.0 size=     212kB time=00:00:02.70 bitrate= 642.8kbits/frame=   97 fps= 31 q=-0.0 size=     219kB time=00:00:03.20 bitrate= 559.4kbits/frame=  113 fps= 31 q=-0.0 size=     226kB time=00:00:03.73 bitrate= 495.5kbits/frame=  129 fps= 31 q=-0.0 size=     359kB time=00:00:04.27 bitrate= 688.3kbits/frame=  144 fps= 31 q=-0.0 size=     367kB time=00:00:04.77 bitrate= 630.1kbits/frame=  159 fps= 31 q=-0.0 size=     373kB time=00:00:05.27 bitrate= 580.1kbits/frame=  174 fps= 31 q=-0.0 size=     477kB time=00:00:05.77 bitrate= 676.5kbits/frame=  190 fps= 31 q=-0.0 size=     644kB time=00:00:06.30 bitrate= 836.0kbits/frame=  205 fps= 31 q=-0.0 size=     770kB time=00:00:06.80 bitrate= 926.5kbits/frame=  220 fps= 31 q=-0.0 size=     776kB time=00:00:07.30 bitrate= 870.1kbits/frame=  235 fps= 30 q=-0.0 size=     782kB time=00:00:07.80 bitrate= 820.2kbits/frame=  251 fps= 30 q=-0.0 size=     940kB time=00:00:08.34 bitrate= 923.1kbits/frame=  266 fps= 30 q=-0.0 size=     947kB time=00:00:08.84 bitrate= 877.5kbits/frame=  281 fps= 30 q=-0.0 size=     953kB time=00:00:09.34 bitrate= 836.0kbits/frame=  297 fps= 30 q=-0.0 size=     960kB time=00:00:09.87 bitrate= 796.0kbits/frame=  312 fps= 30 q=-0.0 size=     966kB time=00:00:10.37 bitrate= 762.3kbits/frame=  328 fps= 30 q=-0.0 size=     972kB time=00:00:10.91 bitrate= 729.7kbits/frame=  343 fps= 30 q=-0.0 size=     978kB time=00:00:11.41 bitrate= 701.9kbits/frame=  359 fps= 30 q=-0.0 size=     983kB time=00:00:11.94 bitrate= 674.2kbits/frame=  374 fps= 30 q=-0.0 size=    1148kB time=00:00:12.44 bitrate= 755.7kbits/frame=  390 fps= 30 q=-0.0 size=    1155kB time=00:00:12.97 bitrate= 728.9kbits/frame=  405 fps= 30 q=-0.0 size=    1161kB time=00:00:13.48 bitrate= 705.3kbits/frame=  421 fps= 30 q=-0.0 size=    1167kB time=00:00:14.01 bitrate= 682.1kbits/frame=  436 fps= 30 q=-0.0 size=    1173kB time=00:00:14.51 bitrate= 661.8kbits/frame=  452 fps= 30 q=-0.0 size=    1180kB time=00:00:15.04 bitrate= 642.3kbits/frame=  467 fps= 30 q=-0.0 size=    1186kB time=00:00:15.54 bitrate= 624.9kbits/frame=  483 fps= 30 q=-0.0 size=    1355kB time=00:00:16.08 bitrate= 690.3kbits/frame=  498 fps= 30 q=-0.0 size=    1362kB time=00:00:16.58 bitrate= 672.8kbits/frame=  513 fps= 30 q=-0.0 size=    1369kB time=00:00:17.08 bitrate= 656.4kbits/frame=  529 fps= 30 q=-0.0 size=    1376kB time=00:00:17.61 bitrate= 639.8kbits/frame=  544 fps= 30 q=-0.0 size=    1384kB time=00:00:18.11 bitrate= 625.8kbits/frame=  559 fps= 30 q=-0.0 size=    1391kB time=00:00:18.61 bitrate= 611.8kbits/frame=  575 fps= 30 q=-0.0 size=    1396kB time=00:00:19.15 bitrate= 597.2kbits/frame=  590 fps= 30 q=-0.0 size=    1402kB time=00:00:19.65 bitrate= 584.6kbits/frame=  605 fps= 30 q=-0.0 size=    1571kB time=00:00:20.15 bitrate= 638.7kbits/frame=  608 fps= 30 q=-0.0 Lsize=    1578kB time=00:00:20.25 bitrate= 638.3kbits/s dup=7 drop=5 speed=   1x    
video:1575kB audio:0kB subtitle:0kB other streams:0kB global headers:0kB muxing overhead: 0.201212%
```

But when I try to open the mp4 file(with the default player in ubuntu or VLC) , after pressing "q" to stop the recording obviously -and without getting any error during that part-  I see only a black picture without audio


EDIT: I tried add this file as a clip to my editor (KDENLIVE) and it says "clip is invalid and will be removed  from project, although it supports MP4 clips (I created one with OBS and it opened fine)


So I assume B frames are like mandatory to exist in order for the file to be read? is there an other way to make FFMPEG support bframes? buttom line is that I want to capture my screen using the VCE of my graphics card because software redering hits the smoothness and the overall performance in games..

---

