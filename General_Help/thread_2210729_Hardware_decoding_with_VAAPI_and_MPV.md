---
title: "Hardware decoding with VAAPI and MPV"
date: 2014-03-12
forum: General Help
---

### Post by cgerrie on 2014-03-12
Hello. I have a laptop with ubuntu 13.10 installed. It has an AMD graphics card, and I would like to use vaapi to decode video in hardware. However, whenever I try to watch a video with hardware decoding enabled, I get errors, and it says that it is  switching to software.

Here is an example:
```

~ $ mpv --hwdec=vaapi -vo opengl-hq /data/anime/\[coldhell\]_Chu2byo_demo_KOI_ga_shitai_1080p/\[coldhell\]_Chu2byo_demo_KOI_ga_shitai_NCEDv2_\[URW\]\[B6554957\].mkv
Playing: /data/anime/[coldhell]_Chu2byo_demo_KOI_ga_shitai_1080p/[coldhell]_Chu2byo_demo_KOI_ga_shitai_NCEDv2_[URW][B6554957].mkv
Detected file format: Matroska
File tags:
 TITLE: Chu-2 byo demo KOI ga shitai - NCED
[stream] Video (+) --vid=1 '10bit H.264' (h264)
[stream] Audio (+) --aid=1 --alang=jpn (*) '24bit FLAC 2.0' (flac)
[stream] Subs  (+) --sid=1 --slang=eng (*) 'URW' (ass)
libva info: VA-API version 0.33.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so
libva info: Found init function __vaDriverInit_0_32
libva info: va_openDriver() returns 0
Trying to use hardware decoding.
Selected video codec: H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10 [lavc:h264]
Selected audio codec: FLAC (Free Lossless Audio Codec) [lavc:flac]
AO: [pulse] 48000Hz stereo 2ch s32
[ffmpeg/video] h264: get_buffer() failed
[ffmpeg/video] h264: thread_get_buffer() failed
[ffmpeg/video] h264: decode_slice_header error
[ffmpeg/video] h264: no frame!
Error while decoding frame!
Error using hardware decoding, falling back to software decoding.
AV: 00:00:00 / 00:01:31 (0%) A-V:  0.000
VO: [opengl-hq] 1920x1080 => 1920x1080 420p10
AV: 00:00:05 / 00:01:31 (6%) A-V:  0.001




Exiting... (Quit)
Segmentation fault (core dumped)


~ $ 



```

And here is fglrxinfo:
```

~ $ fglrxinfo
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 7640G
OpenGL version string: 4.2.12337 Compatibility Profile Context 13.101


~ $ 



```

Any help is appreciated, and I can provide more information if need be.
Thank you in advance, cgerrie.

---

### Post by monkeybrain20122 on 2014-03-12
Hi,

How did you install mpv? I read in the mpv list that vaapi is only supported if you install from git but not in the stable version (But I am not sure if it has a stable release)
It works for me but it is intel graphic rather than amd, I put this in the config file in  .mpv,
```
[default]
vo=vaapi

[vo.vaapi]
hwdec=vaapi

softvol=yes
softvol-max=600
```

The last two lines are for soft volume control, they have nothing to do with vaapi.

You may want to post the output of vainfo

---

### Post by cgerrie on 2014-03-12
I think I found a ppa that had it, but I'll try compiling the newest one from git.

heres vainfo:
```

~ $ vainfo
libva info: VA-API version 0.33.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so
libva info: Found init function __vaDriverInit_0_32
libva info: va_openDriver() returns 0
vainfo: VA-API version: 0.33 (libva 1.1.1)
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.7.8
vainfo: Supported profile and entrypoints
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD
~ $ 

```

---

### Post by cgerrie on 2014-03-12
Okay I got it working...sorta. It doesn't work with a bunch of my MKVs (due to them being having 10-bit color). Also, if I use a vo other than vaapi, all the colors get reversed(you're supposed to be able to use opengl as well). But it does work. I think what happened was I didn't have xvba-va-driver installed(?), which is necessary.
At any rate, thank you very much monkeybrain20122 for your help. I sincerely appreciate it.

---

