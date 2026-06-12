---
title: "videos wont consitently play"
date: 2023-03-12
forum: General Help
---

### Post by guine on 2023-03-12
I am unable to consistently get videos to play on my computer. If I try to open videos with totem it just flashes up and then disappears with .mp4 files and most .mov files(if I try opening up totem on its own and then open the video it just disappears then too). If I try VLC player it will consistently give me audio with .mp4 and .mov files but will only occasionally give me video and if a file plays with video and then I close it and reopen the same file again I will usually only get audio. I've tried changing video output to x11 but that hasn't made a difference. I have no issues with playing these same file with video editors such as davinci resolve and shotcut which both give me video and audio. I have ubuntu-restricted-extras installed as well and am running 22.10. I have a NVIDIA GeForce RTX™ 3050 Laptop GPU with nvidia driver 510.108.03. Any ideas what is going on and how to fix it?
Thanks

---

### Post by SeijiSensei on 2023-03-12
Try mpv as the player engine with smplayer as the front end.
```
sudo apt install mpv smplayer
```

You can play a video from the command prompt and get very verbose output with
```
mpv --v /path/to/video.mp4
```

---

### Post by guine on 2023-03-13
Thanks, I was able to play a number of videos of multiple file types repeatedly with that. I did run it in the terminal just to see if there was anything there and got this:

```
[cplayer] Command line options: '--v' 'Videos/2022/06-20-2022 beaver lake/DSC_5012.MOV'
[cplayer] mpv 0.34.1 Copyright © 2000-2021 mpv/MPlayer/mplayer2 projects
[cplayer]  built on UNKNOWN
[cplayer] FFmpeg library versions:
[cplayer]    libavutil       57.17.100 (runtime 57.28.100)
[cplayer]    libavcodec      59.18.100 (runtime 59.37.100)
[cplayer]    libavformat     59.16.100 (runtime 59.27.100)
[cplayer]    libswscale      6.4.100 (runtime 6.7.100)
[cplayer]    libavfilter     8.24.100 (runtime 8.44.100)
[cplayer]    libswresample   4.3.100 (runtime 4.7.100)
[cplayer] FFmpeg version: 5.1.1-1ubuntu1
[cplayer] 
[cplayer] Configuration: ./waf configure --prefix=/usr --libdir=/usr/lib/x86_64-linux-gnu --confdir=/etc/mpv --zshdir=/usr/share/zsh/vendor-completions --enable-cdda --enable-dvdnav --enable-libmpv-shared --enable-sdl2 --disable-build-date --enable-dvbin
[cplayer] List of enabled features: alsa asm caca cdda cplayer cplugins cuda-hwaccel cuda-interop debug-build drm dvbin dvdnav egl egl-drm egl-helpers egl-x11 ffmpeg ffmpeg-aviocontext-bytes-read ffnvcodec gbm gbm.h gl gl-wayland glibc-thread-name glob glob-posix gpl iconv jack javascript jpeg lcms2 libarchive libass libavdevice libbluray libdl libm libmpv-shared libplacebo librt linux-fstatfs linux-input-event-codes lua lua52 memfd_create optimize plain-gl posix posix-or-mingw pthreads pulse rubberband sdl2 sdl2-audio sdl2-gamepad sdl2-video sixel spirv-cross spirv-cross-shared stdatomic uchardet vaapi vaapi-drm vaapi-egl vaapi-vulkan vaapi-wayland vaapi-x-egl vaapi-x11 vdpau vector vt.h vulkan wayland wayland-protocols x11 xv zimg zlib
[cplayer] Reading config file /etc/mpv/encoding-profiles.conf
[cplayer] Applying profile 'default'...
[cplayer] Reading config file /etc/mpv/mpv.conf
[cplayer] Applying profile 'default'...
[cplayer] Setting option 'hwdec' = 'vaapi' (flags = 4)
[cplayer] Setting option 'v' = '' (flags = 8)
[cplayer] Waiting for scripts...
[osd/libass] libass API version: 0x1600000
[osd/libass] libass source: tarball: 0.16.0
[osd/libass] Shaper: FriBidi 1.0.8 (SIMPLE) HarfBuzz-ng 2.7.4 (COMPLEX)
[osd/libass] Setting up fonts...
[osd/libass] Using font provider fontconfig
[osd/libass] Done.
[cplayer] Set property: shared-script-properties -> 1
[cplayer] Set property: shared-script-properties -> 1
[cplayer] Done loading scripts.
[cplayer] Running hook: ytdl_hook/on_load
[ytdl_hook] ytdl:// hook 
[ytdl_hook] not a ytdl:// url 
[cplayer] Set property: shared-script-properties -> 1
[ifo_dvdnav] Opening Videos/2022/06-20-2022 beaver lake/DSC_5012.MOV
[bdmv/bluray] Opening Videos/2022/06-20-2022 beaver lake/DSC_5012.MOV
[file] Opening Videos/2022/06-20-2022 beaver lake/DSC_5012.MOV
[demux] Trying demuxers for level=normal.
[cplayer] Set property: shared-script-properties -> 1
[osd/libass] libass API version: 0x1600000
[osd/libass] libass source: tarball: 0.16.0
[osd/libass] Shaper: FriBidi 1.0.8 (SIMPLE) HarfBuzz-ng 2.7.4 (COMPLEX)
[osd/libass] Setting up fonts...
[lavf] Found 'mov,mp4,m4a,3gp,3g2,mj2' at score=100 size=2048.
[file] stream level seek from 131072 to 50722054
[file] stream level seek from 50853126 to 50998362
[demux] Detected file format: mov,mp4,m4a,3gp,3g2,mj2 (libavformat)
[cplayer] Opening done: Videos/2022/06-20-2022 beaver lake/DSC_5012.MOV
[osd/libass] Using font provider fontconfig
[osd/libass] Done.
[find_files] Loading external files in Videos/2022/06-20-2022 beaver lake/
[cplayer] Running hook: ytdl_hook/on_preloaded
[lavf] select track 0
[lavf] select track 1
[cplayer]  (+) Video --vid=1 (*) (h264 1920x1080 59.940fps)
[cplayer]  (+) Audio --aid=1 --alang=eng (*) (pcm_s16le 2ch 48000Hz)
[vo/gpu] Probing for best GPU context.
[vo/gpu/opengl] Initializing GPU context 'wayland'
[vo/gpu/opengl] Initializing GPU context 'x11egl'
[vo/gpu/x11] X11 opening display: :1
[vo/gpu/x11] Display 0 (eDP-1-1): [0, 0, 3840, 2400] @ 60.000378 FPS
[vo/gpu/x11] Current display FPS: 60.000378
[vo/gpu/opengl] EGL_VERSION=1.5
[vo/gpu/opengl] EGL_VENDOR=NVIDIA
[vo/gpu/opengl] EGL_CLIENT_APIS=OpenGL_ES OpenGL
[vo/gpu/opengl] Trying to create Desktop OpenGL context.
[vo/gpu/opengl] Choosing visual EGL config 0x28, visual ID 0x2b
[vo/gpu/opengl] GL_VERSION='4.4.0 NVIDIA 510.108.03'
[vo/gpu/opengl] Detected desktop OpenGL 4.4.
[vo/gpu/opengl] GL_VENDOR='NVIDIA Corporation'
[vo/gpu/opengl] GL_RENDERER='NVIDIA GeForce RTX 3050 Laptop GPU/PCIe/SSE2'
[vo/gpu/opengl] GL_SHADING_LANGUAGE_VERSION='4.40 NVIDIA via Cg compiler'
[vo/gpu] Testing FBO format rgba16f
[vo/gpu] Using FBO format rgba16f.
[vo/gpu] No advanced processing required. Enabling dumb mode.
[vo/gpu] Assuming 60.000378 FPS for display sync.
[vd] Container reported FPS: 59.940060
[vd] Codec list:
[vd]     h264 - H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10
[vd]     h264_v4l2m2m (h264) - V4L2 mem2mem H.264 decoder wrapper
[vd]     h264_qsv (h264) - H264 video (Intel Quick Sync Video acceleration)
[vd]     h264_cuvid (h264) - Nvidia CUVID H264 decoder
[vd] Opening decoder h264
[vd] Looking at hwdec h264-vaapi...
[vo/gpu] Loading hwdec driver 'vaapi-egl'
[vo/gpu/vaapi-egl] using VAAPI EGL interop
[vo/gpu/vaapi-egl] Trying to open a x11 VA display...
[vo/gpu] Loading failed.
[vo/gpu] Loading hwdec driver 'cuda-nvdec'
[vo/gpu/cuda-nvdec] cu->cuInit(0) failed -> CUDA_ERROR_UNKNOWN: unknown error
[vo/gpu] Loading failed.
[vo/gpu] Loading hwdec driver 'drmprime-drm'
[vo/gpu/drmprime-drm] Failed to retrieve DRM fd from native display.
[vo/gpu] Loading failed.
[vd] Could not create device.
[vd] No hardware decoding available for this codec.
[vd] Using software decoding.
[vd] Detected 8 logical cores.
[vd] Requesting 9 threads for decoding.
[vd] Selected codec: h264 (H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10)
[vf] User filter list:
[vf]   (empty)
[ad] Codec list:
[ad]     pcm_s16le - PCM signed 16-bit little-endian
[ad] Opening decoder pcm_s16le
[ad] Requesting 1 threads for decoding.
[ad] Selected codec: pcm_s16le (PCM signed 16-bit little-endian)
[af] User filter list:
[af]   (empty)
[cplayer] Starting playback...
[file] stream level seek from 50998362 to 32
[vd] Using software decoding.
[vd] Decoder format: 1920x1080 [0:1] yuv420p bt.601/bt.709/gamma2.2/full/auto CL=mpeg2/4/h264
[vf] [in] 1920x1080 yuv420p bt.601/bt.709/gamma2.2/full/display SP=1.000000 CL=mpeg2/4/h264
[vf] [userdeint] 1920x1080 yuv420p bt.601/bt.709/gamma2.2/full/display SP=1.000000 CL=mpeg2/4/h264
[vf] [userdeint] (disabled)
[vf] [autorotate] 1920x1080 yuv420p bt.601/bt.709/gamma2.2/full/display SP=1.000000 CL=mpeg2/4/h264
[vf] [autorotate] (disabled)
[vf] [convert] 1920x1080 yuv420p bt.601/bt.709/gamma2.2/full/display SP=1.000000 CL=mpeg2/4/h264
[vf] [convert] (disabled)
[vf] [out] 1920x1080 yuv420p bt.601/bt.709/gamma2.2/full/display SP=1.000000 CL=mpeg2/4/h264
[af] [in] 48000Hz stereo 2ch s16
[af] [userspeed] 48000Hz stereo 2ch s16
[af] [userspeed] (disabled)
[af] [convert] 48000Hz stereo 2ch s16
[ao] Trying audio driver 'pulse'
[ao/pulse] requested format: 48000 Hz, stereo channels, s16
[ao/pulse] Library version: 16.1.0
[ao/pulse] Proto: 35
[ao/pulse] Server proto: 4294967295
[ao/pulse] Channel layouts:
[ao/pulse]  - #fl
[ao/pulse]  - #fr
[ao/pulse]  - #fc
[ao/pulse]  - #lfe
[ao/pulse]  - #bl
[ao/pulse]  - #br
[ao/pulse]  - #flc
[ao/pulse]  - #frc
[ao/pulse]  - #bc
[ao/pulse]  - #sl
[ao/pulse]  - #sr
[ao/pulse]  - #tc
[ao/pulse]  - #tfl
[ao/pulse]  - #tfc
[ao/pulse]  - #tfr
[ao/pulse]  - #tbl
[ao/pulse]  - #tbc
[ao/pulse]  - #tbr
[ao/pulse] result: stereo
[ao/pulse] device buffer: 4800 samples.
[ao/pulse] using soft-buffer of 9600 samples.
[cplayer] AO: [pulse] 48000Hz stereo 2ch s16
[cplayer] AO: Description: PulseAudio audio output
[af] [convert] (disabled)
[af] [out] 48000Hz stereo 2ch s16
[cplayer] VO: [gpu] 1920x1080 yuv420p
[cplayer] VO: Description: Shader-based GPU Renderer
[vo/gpu] reconfig to 1920x1080 yuv420p bt.601/bt.709/gamma2.2/full/display SP=1.000000 CL=mpeg2/4/h264
[vo/gpu/x11] not waiting for MapNotify
[vo/gpu] Resize: 1920x1080
[vo/gpu] Window size: 1920x1080 (Borders: l=0 t=0 r=0 b=0)
[vo/gpu] Video source: 1920x1080 (1:1)
[vo/gpu] Video display: (0, 0) 1920x1080 -> (0, 0) 1920x1080
[vo/gpu] Video scale: 1.000000/1.000000
[vo/gpu] OSD borders: l=0 t=0 r=0 b=0
[vo/gpu] Video borders: l=0 t=0 r=0 b=0
[vo/gpu] Reported display depth: 8
[vo/gpu] Texture for plane 0: 1920x1080
[vo/gpu] Texture for plane 1: 960x540
[vo/gpu] Texture for plane 2: 960x540
[vo/gpu] Testing FBO format rgba16f
[vo/gpu] Using FBO format rgba16f.
[vo/gpu] No advanced processing required. Enabling dumb mode.
[vo/gpu] DR enabled: yes
[cplayer] first video frame after restart shown
[cplayer] Set property: shared-script-properties -> 1
[cplayer] audio ready
[cplayer] delaying audio start 0.000000 vs. 0.000000, diff=0.000000
[cplayer] playback restart complete @ 0.000000, audio=ready, video=playing
[vo/gpu/x11] Disabling screensaver.
[statusline] AV: 00:00:00 / 00:00:11 (0%) A-V:  0.000
[cplayer] starting audio playback
[ao/pulse] starting AO
[statusline] AV: 00:00:00 / 00:00:11 (0%) A-V:  0.000
[cplayer] Set property: shared-script-properties -> 1
[statusline] AV: 00:00:01 / 00:00:11 (11%) A-V:  0.000
[cplayer] Set property: shared-script-properties -> 1
[statusline] AV: 00:00:01 / 00:00:11 (11%) A-V:  0.000
[osd/libass] fontselect: (sans-serif, 400, 0) -> /usr/share/fonts/truetype/dejavu/DejaVuSans.ttf, 0, DejaVuSans
[osd/libass] fontselect: (mpv-osd-symbols, 400, 0) -> mpv-osd-symbols-Regular, 0, mpv-osd-symbols-Regular
[vo/gpu] Reallocating OSD texture to 2048x256.
[statusline] AV: 00:00:01 / 00:00:11 (13%) A-V:  0.000
[cplayer] Set property: shared-script-properties -> 1
[statusline] AV: 00:00:09 / 00:00:11 (88%) A-V:  0.000
[lavf] EOF reached.
[statusline] AV: 00:00:10 / 00:00:11 (97%) A-V:  0.000
[af] filter input EOF
[af] filter output EOF
[cplayer] audio filter EOF
[cplayer] audio draining
[cplayer] audio EOF reached
[statusline] AV: 00:00:10 / 00:00:11 (99%) A-V:  0.000
[ao/pulse] audio end or underrun
[statusline] AV: 00:00:11 / 00:00:11 (100%) A-V:  0.000
[vf] filter input EOF
[vf] filter output EOF
[statusline] AV: 00:00:11 / 00:00:11 (100%) A-V:  0.000
[cplayer] EOF code: 1  
[cplayer] finished playback, success (reason 0)
[cplayer] 
[cplayer] Exiting... (End of file)
[cplayer] Set property: shared-script-properties -> 1
[cplayer] draining left over audio
[vo/gpu/x11] Enabling screensaver.
[ao/pulse] audio end or underrun
```

There were a couple of things I saw that failed to load but not sure if thats a rabbit hole worth going down if I can play videos and I had some CUDA issues with getting my GPU up and running last year and was told that the problems I was having with that was a known issue so there may not be anything that can be done until the nvidia drivers work there way into ubuntu.

---

### Post by SeijiSensei on 2023-03-14
Play around in the settings in smplayer. Under Options > Preferences > General > Video you can choose various video output drivers. With NVIDIA you should give "vdpau" a try assuming you've installed and are using the NVIDIA driver. If not, I recommend running
```
sudo ubuntu-drivers
```
It should see your video card and install the appropriate driver.

---

### Post by DuckHook on 2023-03-14
At the risk of muddying SeijiSensei's good advice, another player I've really appreciated is VLC.

This one will often play formats for me that other players can't. This is because VLC comes bundled with many built&#8209;in codecs that may be missing from your system.

---

### Post by SeijiSensei on 2023-03-15
> **guine said:**
> If I try VLC player it will consistently give me audio with .mp4 and .mov files but will only occasionally give me video and if a file plays with video and then I close it and reopen the same file again I will usually only get audio.
He said he had issues with VLC. I find mpv will play pretty much anything I throw at it.

I used to use mplayer back in the day and found it was the best overall video player at the time. mpv is the successor to mplayer. In fact, smplayer is called that because it originally used the mplayer engine. The "s" stood for the fact that it could handle embedded subtitles like those found in mkv files.

---

### Post by DuckHook on 2023-03-15
> **SeijiSensei said:**
> He said he had issues with VLC.
Apologies to all.

My bad. I read as far as Totem and missed the VLC reference.

Note to self: Read thoroughly before responding.

---

### Post by guine on 2023-03-15
I already had vdpau installed and with changing the output from default to vdpau it again played normally with video and audio with the only errors that I could see in terminal being the same couple of things failed in this section:
```
[vo/gpu] Loading hwdec driver 'vaapi-egl'
[vo/gpu/vaapi-egl] using VAAPI EGL interop
[vo/gpu/vaapi-egl] Trying to open a x11 VA display...
[vo/gpu] Loading failed.
[vo/gpu] Loading hwdec driver 'cuda-nvdec'
[vo/gpu] Loading hwdec driver 'drmprime-drm'
[vo/gpu/drmprime-drm] Failed to retrieve DRM fd from native display.
[vo/gpu] Loading failed.
```
And like the previous times I wouldn't have thought anything was wrong if I hadn't been looking through the output in the terminal so I'm not sure if these are errors that I should be worrying about or just the software seeing what I have on my computer to figure out how to process everything.

---

### Post by MAFoElffen on 2023-03-15
From what I saw there their GitHub Issues, is that the message "Failed to retrieve DRM fd from native display" is going to be a normal message logged as it tries different drivers to display a video. The users were told that that is normal in the driver probes, and to ignore it. (Then the noted 'issues' were closed out.) It didn't seem to be a problem indicating that something was fatally wrong and wouldn't display the video. There was a suggestion that maybe this specific message shouldn't be displayed in the logs, because it alarmed Users to a possible problem that really isn't there .

RE: [https://github.com/mpv-player/mpv/issues/5857](https://github.com/mpv-player/mpv/issues/5857)

---

### Post by guine on 2023-03-16
Thanks for the info, good to know I don't need to worry about it.

---

