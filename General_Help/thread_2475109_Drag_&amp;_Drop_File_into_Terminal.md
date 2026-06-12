---
title: "Drag &amp; Drop File into Terminal"
date: 2022-05-17
forum: General Help
---

### Post by Quarkrad on 2022-05-17
I have many old vhs video tapes that I have digitised. On some digitised videos there is a black boarder on some sides and on quite a few videos a fuzziness at the bottom.  I am happy to crop these videos by 20 pixels on each size and have written a small bash script that will do this for me.

 ```
#!/bin/bash
read -p "enter file name: " name
ffmpeg -i $name -filter:v "crop=in_w-2*20:in_h-2*20" /media/dad/workspace/julie/output.mkv
```

At first this did not work because when I dragged the file name (the file I want cropping - 20sec.mkv) into the terminal only the file name was copied - now, thanks to help from yetimon_64, I have amended caja so that the full path name is copied.  When I copy/paste the file name into my script it works:

```
dad@dadubuntu:~/Desktop$ ./crop.sh
enter file name: file:///media/dad/workspace/julie/20sec.mkv 
ffmpeg version 4.4.1-3ubuntu5 Copyright (c) 2000-2021 the FFmpeg developers
  built with gcc 11 (Ubuntu 11.2.0-18ubuntu1)
  configuration: --prefix=/usr --extra-version=3ubuntu5 --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --arch=amd64 --enable-gpl --disable-stripping --enable-gnutls --enable-ladspa --enable-libaom --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libcodec2 --enable-libdav1d --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libjack --enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librabbitmq --enable-librubberband --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libsrt --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvidstab --enable-libvorbis --enable-libvpx --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzimg --enable-libzmq --enable-libzvbi --enable-lv2 --enable-omx --enable-openal --enable-opencl --enable-opengl --enable-sdl2 --enable-pocketsphinx --enable-librsvg --enable-libmfx --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libx264 --enable-shared
  WARNING: library configuration mismatch
  avcodec     configuration: --prefix=/usr --extra-version=3ubuntu5 --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --arch=amd64 --enable-gpl --disable-stripping --enable-gnutls --enable-ladspa --enable-libaom --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libcodec2 --enable-libdav1d --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libjack --enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librabbitmq --enable-librubberband --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libsrt --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvidstab --enable-libvorbis --enable-libvpx --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzimg --enable-libzmq --enable-libzvbi --enable-lv2 --enable-omx --enable-openal --enable-opencl --enable-opengl --enable-sdl2 --enable-pocketsphinx --enable-librsvg --enable-libmfx --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libx264 --enable-shared --enable-version3 --disable-doc --disable-programs --enable-libaribb24 --enable-libopencore_amrnb --enable-libopencore_amrwb --enable-libtesseract --enable-libvo_amrwbenc --enable-libsmbclient
  libavutil      56. 70.100 / 56. 70.100
  libavcodec     58.134.100 / 58.134.100
  libavformat    58. 76.100 / 58. 76.100
  libavdevice    58. 13.100 / 58. 13.100
  libavfilter     7.110.100 /  7.110.100
  libswscale      5.  9.100 /  5.  9.100
  libswresample   3.  9.100 /  3.  9.100
  libpostproc    55.  9.100 / 55.  9.100
Input #0, matroska,webm, from 'file:///media/dad/workspace/julie/20sec.mkv':
  Metadata:
    ENCODER         : Lavf58.76.100
  Duration: 00:00:20.16, start: 0.000000, bitrate: 2650 kb/s
  Stream #0:0: Video: h264 (High), yuv420p(tv, bt709, progressive), 720x576 [SAR 1:1 DAR 5:4], 25 fps, 25 tbr, 1k tbn, 50 tbc (default)
    Metadata:
      DURATION        : 00:00:20.160000000
  Stream #0:1: Audio: aac (LC), 48000 Hz, stereo, fltp (default)
    Metadata:
      title           : simple_aac
      DURATION        : 00:00:20.010000000
Stream mapping:
  Stream #0:0 -> #0:0 (h264 (native) -> h264 (libx264))
  Stream #0:1 -> #0:1 (aac (native) -> vorbis (libvorbis))
Press [q] to stop, [?] for help
[libx264 @ 0x55c27b8f9d40] using SAR=1/1
[libx264 @ 0x55c27b8f9d40] using cpu capabilities: MMX2 SSE2Fast SSSE3 SSE4.2 AVX FMA3 BMI2 AVX2
[libx264 @ 0x55c27b8f9d40] profile High, level 3.0, 4:2:0, 8-bit
[libx264 @ 0x55c27b8f9d40] 264 - core 163 r3060 5db6aa6 - H.264/MPEG-4 AVC codec - Copyleft 2003-2021 - http://www.videolan.org/x264.html - options: cabac=1 ref=3 deblock=1:0:0 analyse=0x3:0x113 me=hex subme=7 psy=1 psy_rd=1.00:0.00 mixed_ref=1 me_range=16 chroma_me=1 trellis=1 8x8dct=1 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=-2 threads=12 lookahead_threads=2 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=3 b_pyramid=2 b_adapt=1 b_bias=0 direct=1 weightb=1 open_gop=0 weightp=2 keyint=250 keyint_min=25 scenecut=40 intra_refresh=0 rc_lookahead=40 rc=crf mbtree=1 crf=23.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 ip_ratio=1.40 aq=1:1.00
Output #0, matroska, to '/media/dad/workspace/julie/output.mkv':
  Metadata:
    encoder         : Lavf58.76.100
  Stream #0:0: Video: h264 (H264 / 0x34363248), yuv420p(tv, bt709, progressive), 680x536 [SAR 1:1 DAR 85:67], q=2-31, 25 fps, 1k tbn (default)
    Metadata:
      DURATION        : 00:00:20.160000000
      encoder         : Lavc58.134.100 libx264
    Side data:
      cpb: bitrate max/min/avg: 0/0/0 buffer size: 0 vbv_delay: N/A
  Stream #0:1: Audio: vorbis (oV[0][0] / 0x566F), 48000 Hz, stereo, fltp (default)
    Metadata:
      title           : simple_aac
      DURATION        : 00:00:20.010000000
      encoder         : Lavc58.134.100 libvorbis
frame=    1 fps=0.0 q=0.0 size=       5kB time=00:00:00.24 bitrate= 158.8kbits/sframe=  169 fps=0.0 q=28.0 size=       5kB time=00:00:06.97 bitrate=   5.5kbits/frame=  311 fps=306 q=28.0 size=    1024kB time=00:00:12.73 bitrate= 658.7kbits/frame=  447 fps=294 q=28.0 size=    2048kB time=00:00:18.11 bitrate= 926.1kbits/frame=  502 fps=269 q=-1.0 Lsize=    4006kB time=00:00:20.00 bitrate=1640.2kbits/s speed=10.7x    
video:3771kB audio:219kB subtitle:0kB other streams:0kB global headers:4kB muxing overhead: 0.383436%
[libx264 @ 0x55c27b8f9d40] frame I:4     Avg QP:23.25  size: 24998
[libx264 @ 0x55c27b8f9d40] frame P:131   Avg QP:24.43  size: 13980
[libx264 @ 0x55c27b8f9d40] frame B:367   Avg QP:26.22  size:  5259
[libx264 @ 0x55c27b8f9d40] consecutive B-frames:  2.0%  1.2%  1.2% 95.6%
[libx264 @ 0x55c27b8f9d40] mb I  I16..4: 14.5% 70.4% 15.1%
[libx264 @ 0x55c27b8f9d40] mb P  I16..4:  8.2% 24.4%  6.0%  P16..4: 38.9% 13.5%  5.1%  0.0%  0.0%    skip: 3.8%
[libx264 @ 0x55c27b8f9d40] mb B  I16..4:  0.6%  1.2%  0.4%  B16..8: 37.0%  7.8%  1.6%  direct: 9.7%  skip:41.7%  L0:41.1% L1:43.7% BI:15.2%
[libx264 @ 0x55c27b8f9d40] 8x8 transform intra:62.8% inter:66.4%
[libx264 @ 0x55c27b8f9d40] coded y,uvDC,uvAC intra: 56.3% 68.4% 22.3% inter: 24.6% 37.7% 0.6%
[libx264 @ 0x55c27b8f9d40] i16 v,h,dc,p: 38% 20% 12% 30%
[libx264 @ 0x55c27b8f9d40] i8 v,h,dc,ddl,ddr,vr,hd,vl,hu: 26% 15% 23%  6%  6%  6%  5%  7%  6%
[libx264 @ 0x55c27b8f9d40] i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 19% 38% 15%  4%  5%  4%  5%  4%  5%
[libx264 @ 0x55c27b8f9d40] i8c dc,h,v,p: 54% 18% 20%  8%
[libx264 @ 0x55c27b8f9d40] Weighted P-Frames: Y:9.9% UV:2.3%
[libx264 @ 0x55c27b8f9d40] ref P L0: 55.1% 14.3% 19.8% 10.4%  0.5%
[libx264 @ 0x55c27b8f9d40] ref B L0: 91.0%  6.9%  2.1%
[libx264 @ 0x55c27b8f9d40] ref B L1: 98.2%  1.8%
[libx264 @ 0x55c27b8f9d40] kb/s:1529.22

```

I now have a cropped video called output.mkv - in this example in /media/dad/workspace/julie/

When I run the same script, but this time dragging the file name from caja into the terminal, the script does not produce an output:

```
dad@dadubuntu:~/Desktop$ ./crop.sh
enter file name: '/media/dad/workspace/julie/20sec.mkv' 
ffmpeg version 4.4.1-3ubuntu5 Copyright (c) 2000-2021 the FFmpeg developers
  built with gcc 11 (Ubuntu 11.2.0-18ubuntu1)
  configuration: --prefix=/usr --extra-version=3ubuntu5 --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --arch=amd64 --enable-gpl --disable-stripping --enable-gnutls --enable-ladspa --enable-libaom --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libcodec2 --enable-libdav1d --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libjack --enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librabbitmq --enable-librubberband --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libsrt --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvidstab --enable-libvorbis --enable-libvpx --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzimg --enable-libzmq --enable-libzvbi --enable-lv2 --enable-omx --enable-openal --enable-opencl --enable-opengl --enable-sdl2 --enable-pocketsphinx --enable-librsvg --enable-libmfx --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libx264 --enable-shared
  WARNING: library configuration mismatch
  avcodec     configuration: --prefix=/usr --extra-version=3ubuntu5 --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --arch=amd64 --enable-gpl --disable-stripping --enable-gnutls --enable-ladspa --enable-libaom --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libcodec2 --enable-libdav1d --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libjack --enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librabbitmq --enable-librubberband --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libsrt --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvidstab --enable-libvorbis --enable-libvpx --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzimg --enable-libzmq --enable-libzvbi --enable-lv2 --enable-omx --enable-openal --enable-opencl --enable-opengl --enable-sdl2 --enable-pocketsphinx --enable-librsvg --enable-libmfx --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libx264 --enable-shared --enable-version3 --disable-doc --disable-programs --enable-libaribb24 --enable-libopencore_amrnb --enable-libopencore_amrwb --enable-libtesseract --enable-libvo_amrwbenc --enable-libsmbclient
  libavutil      56. 70.100 / 56. 70.100
  libavcodec     58.134.100 / 58.134.100
  libavformat    58. 76.100 / 58. 76.100
  libavdevice    58. 13.100 / 58. 13.100
  libavfilter     7.110.100 /  7.110.100
  libswscale      5.  9.100 /  5.  9.100
  libswresample   3.  9.100 /  3.  9.100
  libpostproc    55.  9.100 / 55.  9.100
'/media/dad/workspace/julie/20sec.mkv': No such file or directory

```

I am happy with the *copy/paste* method but obviously *drag & drop* into the terminal is quicker and I am now use to using this method as I use the terminal more and more. I do not know why this script works when I paste the input file name (/media/dad/workspace/julie/20sec.mkv) into the terminal but not when it is drag and dropped.

---

### Post by &amp;KyT$0P# on 2022-05-17
As a test, any difference if you delete the enclosing single-quotes?
If that works, can you edit your [FONT=Courier New]crop.sh[/FONT] to take the file name as a command-line argument?

---

### Post by Impavidus on 2022-05-17
There are two differences between the filenames. In the one that works, you have a file:// prefix. If only one of them worked, I would expect the one with the prefix to fail, but it's the other way around. The other difference are the single quote characters. If you entered the filename as a command line argument, bash would remove the quote characters (but keep any special characters in the name). However, you don't give the filename as a command line argument to the script, but you have the script prompt for the filename. Bash will just store it as a single string, without any processing to break it into arguments and without removing the quote characters. Confusingly, ffmpeg automatically adds the same quote characters in all its output except in the no such file message.

---

### Post by Quarkrad on 2022-05-18
Afraid I'm struggling with this - spent a lot of time reading and reading.  I do not know how to change my script so that the *dragged filename* is a command line argument.

---

### Post by Quarkrad on 2022-05-18
Ok - I've got something to work - the script now looks like:

```
#!/bin/bash 
ffmpeg -i $1 -filter:v "crop=in_w-2*20:in_h-2*20" /media/dad/workspace/julie/output.mkv
```

output is :

```
dad@dadubuntu:~$ cd Desktop
dad@dadubuntu:~/Desktop$ ./crop.sh '/media/dad/workspace/julie/20sec.mkv' 
ffmpeg version 4.4.1-3ubuntu5 Copyright (c) 2000-2021 the FFmpeg developers
  built with gcc 11 (Ubuntu 11.2.0-18ubuntu1)
  configuration: --prefix=/usr --extra-version=3ubuntu5 --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --arch=amd64 --enable-gpl --disable-stripping --enable-gnutls --enable-ladspa --enable-libaom --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libcodec2 --enable-libdav1d --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libjack --enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librabbitmq --enable-librubberband --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libsrt --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvidstab --enable-libvorbis --enable-libvpx --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzimg --enable-libzmq --enable-libzvbi --enable-lv2 --enable-omx --enable-openal --enable-opencl --enable-opengl --enable-sdl2 --enable-pocketsphinx --enable-librsvg --enable-libmfx --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libx264 --enable-shared
  WARNING: library configuration mismatch
  avcodec     configuration: --prefix=/usr --extra-version=3ubuntu5 --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --arch=amd64 --enable-gpl --disable-stripping --enable-gnutls --enable-ladspa --enable-libaom --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libcodec2 --enable-libdav1d --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libjack --enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librabbitmq --enable-librubberband --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libsrt --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvidstab --enable-libvorbis --enable-libvpx --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzimg --enable-libzmq --enable-libzvbi --enable-lv2 --enable-omx --enable-openal --enable-opencl --enable-opengl --enable-sdl2 --enable-pocketsphinx --enable-librsvg --enable-libmfx --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libx264 --enable-shared --enable-version3 --disable-doc --disable-programs --enable-libaribb24 --enable-libopencore_amrnb --enable-libopencore_amrwb --enable-libtesseract --enable-libvo_amrwbenc --enable-libsmbclient
  libavutil      56. 70.100 / 56. 70.100
  libavcodec     58.134.100 / 58.134.100
  libavformat    58. 76.100 / 58. 76.100
  libavdevice    58. 13.100 / 58. 13.100
  libavfilter     7.110.100 /  7.110.100
  libswscale      5.  9.100 /  5.  9.100
  libswresample   3.  9.100 /  3.  9.100
  libpostproc    55.  9.100 / 55.  9.100
Input #0, matroska,webm, from '/media/dad/workspace/julie/20sec.mkv':
  Metadata:
    ENCODER         : Lavf58.76.100
  Duration: 00:00:20.16, start: 0.000000, bitrate: 2650 kb/s
  Stream #0:0: Video: h264 (High), yuv420p(tv, bt709, progressive), 720x576 [SAR 1:1 DAR 5:4], 25 fps, 25 tbr, 1k tbn, 50 tbc (default)
    Metadata:
      DURATION        : 00:00:20.160000000
  Stream #0:1: Audio: aac (LC), 48000 Hz, stereo, fltp (default)
    Metadata:
      title           : simple_aac
      DURATION        : 00:00:20.010000000
Stream mapping:
  Stream #0:0 -> #0:0 (h264 (native) -> h264 (libx264))
  Stream #0:1 -> #0:1 (aac (native) -> vorbis (libvorbis))
Press [q] to stop, [?] for help
[libx264 @ 0x55e5b2c772c0] using SAR=1/1
[libx264 @ 0x55e5b2c772c0] using cpu capabilities: MMX2 SSE2Fast SSSE3 SSE4.2 AVX FMA3 BMI2 AVX2
[libx264 @ 0x55e5b2c772c0] profile High, level 3.0, 4:2:0, 8-bit
[libx264 @ 0x55e5b2c772c0] 264 - core 163 r3060 5db6aa6 - H.264/MPEG-4 AVC codec - Copyleft 2003-2021 - http://www.videolan.org/x264.html - options: cabac=1 ref=3 deblock=1:0:0 analyse=0x3:0x113 me=hex subme=7 psy=1 psy_rd=1.00:0.00 mixed_ref=1 me_range=16 chroma_me=1 trellis=1 8x8dct=1 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=-2 threads=12 lookahead_threads=2 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=3 b_pyramid=2 b_adapt=1 b_bias=0 direct=1 weightb=1 open_gop=0 weightp=2 keyint=250 keyint_min=25 scenecut=40 intra_refresh=0 rc_lookahead=40 rc=crf mbtree=1 crf=23.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 ip_ratio=1.40 aq=1:1.00
Output #0, matroska, to '/media/dad/workspace/julie/output.mkv':
  Metadata:
    encoder         : Lavf58.76.100
  Stream #0:0: Video: h264 (H264 / 0x34363248), yuv420p(tv, bt709, progressive), 680x536 [SAR 1:1 DAR 85:67], q=2-31, 25 fps, 1k tbn (default)
    Metadata:
      DURATION        : 00:00:20.160000000
      encoder         : Lavc58.134.100 libx264
    Side data:
      cpb: bitrate max/min/avg: 0/0/0 buffer size: 0 vbv_delay: N/A
  Stream #0:1: Audio: vorbis (oV[0][0] / 0x566F), 48000 Hz, stereo, fltp (default)
    Metadata:
      title           : simple_aac
      DURATION        : 00:00:20.010000000
      encoder         : Lavc58.134.100 libvorbis
frame=    1 fps=0.0 q=0.0 size=       5kB time=00:00:00.24 bitrate= 158.8kbits/sframe=  165 fps=0.0 q=28.0 size=       5kB time=00:00:06.82 bitrate=   5.6kbits/frame=  310 fps=307 q=28.0 size=    1024kB time=00:00:12.64 bitrate= 663.6kbits/frame=  447 fps=296 q=28.0 size=    2048kB time=00:00:18.11 bitrate= 926.1kbits/frame=  502 fps=271 q=-1.0 Lsize=    4006kB time=00:00:20.00 bitrate=1640.2kbits/s speed=10.8x    
video:3771kB audio:219kB subtitle:0kB other streams:0kB global headers:4kB muxing overhead: 0.383436%
[libx264 @ 0x55e5b2c772c0] frame I:4     Avg QP:23.25  size: 24998
[libx264 @ 0x55e5b2c772c0] frame P:131   Avg QP:24.43  size: 13980
[libx264 @ 0x55e5b2c772c0] frame B:367   Avg QP:26.22  size:  5259
[libx264 @ 0x55e5b2c772c0] consecutive B-frames:  2.0%  1.2%  1.2% 95.6%
[libx264 @ 0x55e5b2c772c0] mb I  I16..4: 14.5% 70.4% 15.1%
[libx264 @ 0x55e5b2c772c0] mb P  I16..4:  8.2% 24.4%  6.0%  P16..4: 38.9% 13.5%  5.1%  0.0%  0.0%    skip: 3.8%
[libx264 @ 0x55e5b2c772c0] mb B  I16..4:  0.6%  1.2%  0.4%  B16..8: 37.0%  7.8%  1.6%  direct: 9.7%  skip:41.7%  L0:41.1% L1:43.7% BI:15.2%
[libx264 @ 0x55e5b2c772c0] 8x8 transform intra:62.8% inter:66.4%
[libx264 @ 0x55e5b2c772c0] coded y,uvDC,uvAC intra: 56.3% 68.4% 22.3% inter: 24.6% 37.7% 0.6%
[libx264 @ 0x55e5b2c772c0] i16 v,h,dc,p: 38% 20% 12% 30%
[libx264 @ 0x55e5b2c772c0] i8 v,h,dc,ddl,ddr,vr,hd,vl,hu: 26% 15% 23%  6%  6%  6%  5%  7%  6%
[libx264 @ 0x55e5b2c772c0] i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 19% 38% 15%  4%  5%  4%  5%  4%  5%
[libx264 @ 0x55e5b2c772c0] i8c dc,h,v,p: 54% 18% 20%  8%
[libx264 @ 0x55e5b2c772c0] Weighted P-Frames: Y:9.9% UV:2.3%
[libx264 @ 0x55e5b2c772c0] ref P L0: 55.1% 14.3% 19.8% 10.4%  0.5%
[libx264 @ 0x55e5b2c772c0] ref B L0: 91.0%  6.9%  2.1%
[libx264 @ 0x55e5b2c772c0] ref B L1: 98.2%  1.8%
[libx264 @ 0x55e5b2c772c0] kb/s:1529.22
dad@dadubuntu:~/Desktop$ 

```

So I:
launch a terminal
cd into the directory containing crop.sh
enter *./crop.sh*
drag the input file into the terminal
press Enter

To make this shorter my next step was to create a custom launcher in my top panel that would launch my script in a terminal asking me for the input filename - all I have to do is drag the filename into the terminal and press Enter.  I seem to be half way there but need to combine the bash *read* command with what I have.

---

### Post by TheFu on 2022-05-18
If you have a bunch of these things to do, would passing in a list of filenames as the input argument be more efficient?
Nearly all my scripts accept bash filename globbing as the file specification to process each in turn.

The general form of these scripts is ...
```
#!/bin/bash

for FILE in "$@"; do
    # do stuff here on each filename - filename can be absolute, relative, or simple (i.e. current directory(
   echo Working on .... $FILE
   ROOT=${FILE/%.ts/}
   mkvmerge      -o    "${ROOT}.mkv"     "${FILE}"
done
```

Put the script in ~/bin/ ... which should be in your PATH and make it executable.  Run using 
```
$ script  *ts
```
or 
```
$ script  ~/work/*ts
```

There are some assumptions about the allowed filenames, but you can figure those out.

---

### Post by Quarkrad on 2022-05-19
Simple solution in the end.  Installed kitty terminal - does not insert quotes when draging & dropping a filename into it.

---

