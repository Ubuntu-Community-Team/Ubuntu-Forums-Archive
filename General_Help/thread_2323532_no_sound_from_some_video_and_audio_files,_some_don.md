---
title: "no sound from some video and audio files, some don't play"
date: 2016-05-06
forum: General Help
---

### Post by jeff162 on 2016-05-06
I am having trouble with some audio and video files.

.mp3, .avi and .mkv files  play but there's no sound. .mp4 files don't play at all. I haven't tried any other formats.

There is a thread regarding this but I think I was less than clear on it.

[http://ubuntuforums.org/showthread.php?t=2321843](http://ubuntuforums.org/showthread.php?t=2321843)

I've purged any PPAs that might have to do with the problem but it didn't seem to work. Here's some outputs from mpv if helpful:

With .mp4 doesn't play

```
[   0.199][v][cplayer] Command line options: '--log-file=mpv.txt' '--v' 'test.mp4'[   0.199][v][cplayer] mpv git-bda1110 (C) 2000-2016 mpv/MPlayer/mplayer2 projects
[   0.199][v][cplayer]  built on Sat Apr 30 02:41:02 UTC 2016
[   0.227][v][cplayer] ffmpeg library versions:
[   0.228][v][cplayer]    libavutil       55.23.100
[   0.228][v][cplayer]    libavcodec      57.38.100
[   0.228][v][cplayer]    libavformat     57.34.103
[   0.228][v][cplayer]    libswscale      4.1.100
[   0.228][v][cplayer]    libavfilter     6.44.100
[   0.228][v][cplayer]    libswresample   2.0.101
[   0.228][v][cplayer] ffmpeg version: N-79691-g66dd21d
[   0.228][v][cplayer] 
[   0.228][v][cplayer] Configuration: ./waf configure --enable-pdf-build --prefix=/usr --confdir=/etc/mpv
[   0.228][v][cplayer] List of enabled features: alsa any-gl asm atomic-builtins atomics audio-input av-avpacket-int64-duration av-new-pixdesc av-pix-fmt-mmal av-subtitle-nopict av-version-info avcodec-chroma-pos-api avcodec-has-codecpar avcodec-new-codec-api avcodec-profile-name avframe-metadata avframe-skip-samples avutil-has-hwcontext build-date cdda cplayer debug-build dlopen drm dvbin dvdnav dvdread encoding fchmod gl gl-x11 glibc-thread-name glob iconv jack jpeg lcms2 libass libass-osd libav libavdevice libavfilter libbluray libdl libguess libm librt libsmbclient libswresample libv4l2 linux-fstatfs lua nanosleep optimize oss-audio oss-audio-native posix posix-or-mingw posix-spawn pthreads pulse resampler rubberband shm sse4-intrinsics standard-gl subprocess termios tv tv-v4l2 uchardet vaapi vaapi-glx vaapi-hwaccel vaapi-x11 vdpau vdpau-gl-x11 vdpau-hwaccel videodev vt.h x11 xext xinerama xrandr xss xv zlib
[   0.228][v][global] config path: '' -> '/home/theking/.mpv'
[   0.248][v][global] config path: 'mpv.conf' -/-> '/home/theking/.mpv/mpv.conf'
[   0.248][v][global] config path: 'config' -> '/home/theking/.mpv/config'
[   0.254][v][global] config path: 'mpv.conf' -/-> '/etc/mpv/mpv.conf'
[   0.254][v][global] config path: 'config' -/-> '/etc/mpv/config'
[   0.254][v][cplayer] Reading config file /home/theking/.mpv/config
[   0.259][v][cplayer] Setting option 'log-file' = 'mpv.txt' (flags = 8)
[   0.259][v][cplayer] Setting option 'v' = '' (flags = 8)
[   0.260][v][global] config path: 'input.conf' -/-> '/home/theking/.mpv/input.conf'
[   0.260][v][global] config path: 'input.conf' -/-> '/etc/mpv/input.conf'
[   0.260][v][input] Falling back on default (hardcoded) input config
[   0.285][v][osc] Loading script @osc.lua...
[   0.286][v][global] config path: 'scripts' -/-> '/home/theking/.mpv/scripts'
[   0.286][v][global] config path: 'scripts' -/-> '/etc/mpv/scripts'
[   0.286][v][osc] loading mp.defaults
[   0.287][v][osc] loading @osc.lua
[   0.292][v][global] config path: 'lua-settings/osc.conf' -/-> '/home/theking/.mpv/lua-settings/osc.conf'
[   0.292][v][global] config path: 'lua-settings/osc.conf' -/-> '/etc/mpv/lua-settings/osc.conf'
[   0.292][v][osc] lua-settings/osc.conf not found. 
[   0.293][v][cplayer] Run command: define-section, flags=0, args=[showhide, mouse_move script-binding osc/__keybinding1
[   0.293][v][cplayer] mouse_leave script-binding osc/__keybinding2
[   0.293][v][cplayer] , force]
[   0.293][v][cplayer] Run command: enable-section, flags=0, args=[showhide, allow-hide-cursor+allow-vo-dragging]
[   0.293][v][cplayer] Run command: define-section, flags=0, args=[input, mouse_btn0 script-binding osc/__keybinding3
[   0.293][v][cplayer] shift+mouse_btn0 script-binding osc/__keybinding4
[   0.293][v][cplayer] mouse_btn2 script-binding osc/__keybinding5
[   0.293][v][cplayer] mouse_btn0_dbl ignore
[   0.293][v][cplayer] shift+mouse_btn0_dbl ignore
[   0.293][v][cplayer] mouse_btn2_dbl ignore
[   0.293][v][cplayer] , force]
[   0.293][v][cplayer] Run command: enable-section, flags=0, args=[input, ]
[   0.294][v][cplayer] Run command: define-section, flags=0, args=[input_osc, del script-binding osc/__keybinding6
[   0.294][v][cplayer] , default]
[   0.294][v][cplayer] Run command: enable-section, flags=0, args=[input_osc, allow-hide-cursor+allow-vo-dragging]
[   0.294][v][cplayer] Run command: define-section, flags=0, args=[input_forced_osc, , force]
[   0.294][v][cplayer] Run command: enable-section, flags=0, args=[input_forced_osc, allow-hide-cursor+allow-vo-dragging]
[   0.294][v][cplayer] Done loading @osc.lua.
[   0.294][v][ytdl_hook] Loading script @ytdl_hook.lua...
[   0.295][v][global] config path: 'scripts' -/-> '/home/theking/.mpv/scripts'
[   0.295][v][global] config path: 'scripts' -/-> '/etc/mpv/scripts'
[   0.295][v][ytdl_hook] loading mp.defaults
[   0.296][v][cplayer] Run command: disable-section, flags=0, args=[input]
[   0.296][v][ytdl_hook] loading @ytdl_hook.lua
[   0.296][v][global] config path: 'fonts' -/-> '/home/theking/.mpv/fonts'
[   0.296][v][global] config path: 'fonts' -/-> '/etc/mpv/fonts'
[   0.296][v][cplayer] Run command: hook-add, flags=0, args=[on_load, 1, 10]
[   0.297][v][cplayer] Done loading @ytdl_hook.lua.
[   0.297][v][osd/libass] Shaper: FriBidi 0.19.6 (SIMPLE) HarfBuzz-ng 0.9.27 (COMPLEX)
[   0.297][v][global] config path: 'scripts' -/-> '/home/theking/.mpv/scripts'
[   0.297][v][global] config path: 'subfont.ttf' -/-> '/home/theking/.mpv/subfont.ttf'
[   0.297][v][global] config path: 'scripts' -/-> '/etc/mpv/scripts'
[   0.297][v][global] config path: 'subfont.ttf' -/-> '/etc/mpv/subfont.ttf'
[   0.297][v][global] config path: 'watch_later' -> '/home/theking/.mpv/watch_later'
[   0.297][v][global] config path: 'fonts.conf' -/-> '/home/theking/.mpv/fonts.conf'
[   0.297][i][cplayer] Playing: test.mp4
[   0.297][v][cplayer] Running hook: ytdl_hook/on_load
[   0.297][v][global] config path: 'fonts.conf' -/-> '/etc/mpv/fonts.conf'
[   0.297][v][osd/libass] Setting up fonts...
[   0.297][v][cplayer] Run command: hook-ack, flags=0, args=[on_load]
[   0.299][v][ifo] Opening test.mp4
[   0.300][v][ifo/dvdnav] Opening test.mp4
[   0.301][v][bdmv/bluray] Opening test.mp4
[   0.302][v][file] Opening test.mp4
[   0.302][v][file] Stream opened successfully.
[   0.302][v][demux] Trying demuxers for level=normal.
[   0.307][v][osd/libass] Using font provider fontconfig
[   0.307][v][osd/libass] Done.
[   0.626][v][lavf] No format found, try lowering probescore or forcing the format.
[   0.627][v][demux] Trying demuxers for level=unsafe.
[   0.628][v][lavf] Found 'mov,mp4,m4a,3gp,3g2,mj2' at score=1 size=2048.
[   0.628][v][lavf] Found 'mov,mp4,m4a,3gp,3g2,mj2' at score=1 size=4096.
[   0.629][v][lavf] Found 'mov,mp4,m4a,3gp,3g2,mj2' at score=1 size=8192.
[   0.629][v][lavf] Found 'mov,mp4,m4a,3gp,3g2,mj2' at score=1 size=16384.
[   0.631][v][lavf] Found 'mov,mp4,m4a,3gp,3g2,mj2' at score=1 size=32768.
[   0.634][v][lavf] Found 'mov,mp4,m4a,3gp,3g2,mj2' at score=1 size=65536.
[   0.640][v][lavf] Found 'mov,mp4,m4a,3gp,3g2,mj2' at score=1 size=131072.
[   0.652][v][lavf] Found 'mov,mp4,m4a,3gp,3g2,mj2' at score=1 size=262144.
[   0.676][v][lavf] Found 'mov,mp4,m4a,3gp,3g2,mj2' at score=1 size=524288.
[   0.724][v][lavf] Found 'mov,mp4,m4a,3gp,3g2,mj2' at score=1 size=1048576.
[   0.820][v][lavf] Found 'mov,mp4,m4a,3gp,3g2,mj2' at score=1 size=2097152.
[   0.916][v][lavf] Found 'mov,mp4,m4a,3gp,3g2,mj2' at score=1 size=2097152.
[   0.916][v][lavf] No format found, try lowering probescore or forcing the format.
[   0.918][v][cplayer] finished playback, unrecognized file format (reason 4)
[   0.918][e][cplayer] Failed to recognize file format.
[   0.918][i][cplayer] 
[   0.918][i][cplayer] 
[   0.918][i][cplayer] Exiting... (Errors when loading file)
[   0.921][v][ytdl_hook] Exiting...
[   0.923][v][osc] Exiting...
```

With .avi plays but no sound

```
[   0.006][v][cplayer] Command line options: '--log-file=mpv.txt' '--v' 'test.mkv'[   0.006][v][cplayer] mpv git-bda1110 (C) 2000-2016 mpv/MPlayer/mplayer2 projects
[   0.006][v][cplayer]  built on Sat Apr 30 02:41:02 UTC 2016
[   0.006][v][cplayer] ffmpeg library versions:
[   0.006][v][cplayer]    libavutil       55.23.100
[   0.006][v][cplayer]    libavcodec      57.38.100
[   0.006][v][cplayer]    libavformat     57.34.103
[   0.006][v][cplayer]    libswscale      4.1.100
[   0.006][v][cplayer]    libavfilter     6.44.100
[   0.006][v][cplayer]    libswresample   2.0.101
[   0.006][v][cplayer] ffmpeg version: N-79691-g66dd21d
[   0.006][v][cplayer] 
[   0.006][v][cplayer] Configuration: ./waf configure --enable-pdf-build --prefix=/usr --confdir=/etc/mpv
[   0.006][v][cplayer] List of enabled features: alsa any-gl asm atomic-builtins atomics audio-input av-avpacket-int64-duration av-new-pixdesc av-pix-fmt-mmal av-subtitle-nopict av-version-info avcodec-chroma-pos-api avcodec-has-codecpar avcodec-new-codec-api avcodec-profile-name avframe-metadata avframe-skip-samples avutil-has-hwcontext build-date cdda cplayer debug-build dlopen drm dvbin dvdnav dvdread encoding fchmod gl gl-x11 glibc-thread-name glob iconv jack jpeg lcms2 libass libass-osd libav libavdevice libavfilter libbluray libdl libguess libm librt libsmbclient libswresample libv4l2 linux-fstatfs lua nanosleep optimize oss-audio oss-audio-native posix posix-or-mingw posix-spawn pthreads pulse resampler rubberband shm sse4-intrinsics standard-gl subprocess termios tv tv-v4l2 uchardet vaapi vaapi-glx vaapi-hwaccel vaapi-x11 vdpau vdpau-gl-x11 vdpau-hwaccel videodev vt.h x11 xext xinerama xrandr xss xv zlib
[   0.006][v][global] config path: '' -> '/home/theking/.mpv'
[   0.006][v][global] config path: 'mpv.conf' -/-> '/home/theking/.mpv/mpv.conf'
[   0.006][v][global] config path: 'config' -> '/home/theking/.mpv/config'
[   0.006][v][global] config path: 'mpv.conf' -/-> '/etc/mpv/mpv.conf'
[   0.006][v][global] config path: 'config' -/-> '/etc/mpv/config'
[   0.006][v][cplayer] Reading config file /home/theking/.mpv/config
[   0.006][v][cplayer] Setting option 'log-file' = 'mpv.txt' (flags = 8)
[   0.006][v][cplayer] Setting option 'v' = '' (flags = 8)
[   0.007][v][global] config path: 'input.conf' -/-> '/home/theking/.mpv/input.conf'
[   0.007][v][global] config path: 'input.conf' -/-> '/etc/mpv/input.conf'
[   0.007][v][input] Falling back on default (hardcoded) input config
[   0.008][v][osc] Loading script @osc.lua...
[   0.008][v][global] config path: 'scripts' -/-> '/home/theking/.mpv/scripts'
[   0.008][v][global] config path: 'scripts' -/-> '/etc/mpv/scripts'
[   0.008][v][osc] loading mp.defaults
[   0.010][v][osc] loading @osc.lua
[   0.015][v][global] config path: 'lua-settings/osc.conf' -/-> '/home/theking/.mpv/lua-settings/osc.conf'
[   0.015][v][global] config path: 'lua-settings/osc.conf' -/-> '/etc/mpv/lua-settings/osc.conf'
[   0.015][v][osc] lua-settings/osc.conf not found. 
[   0.016][v][cplayer] Run command: define-section, flags=0, args=[showhide, mouse_move script-binding osc/__keybinding1
[   0.016][v][cplayer] mouse_leave script-binding osc/__keybinding2
[   0.016][v][cplayer] , force]
[   0.016][v][cplayer] Run command: enable-section, flags=0, args=[showhide, allow-hide-cursor+allow-vo-dragging]
[   0.016][v][cplayer] Run command: define-section, flags=0, args=[input, mouse_btn0 script-binding osc/__keybinding3
[   0.016][v][cplayer] shift+mouse_btn0 script-binding osc/__keybinding4
[   0.016][v][cplayer] mouse_btn2 script-binding osc/__keybinding5
[   0.016][v][cplayer] mouse_btn0_dbl ignore
[   0.016][v][cplayer] shift+mouse_btn0_dbl ignore
[   0.016][v][cplayer] mouse_btn2_dbl ignore
[   0.016][v][cplayer] , force]
[   0.016][v][cplayer] Run command: enable-section, flags=0, args=[input, ]
[   0.016][v][cplayer] Run command: define-section, flags=0, args=[input_osc, del script-binding osc/__keybinding6
[   0.016][v][cplayer] , default]
[   0.016][v][cplayer] Run command: enable-section, flags=0, args=[input_osc, allow-hide-cursor+allow-vo-dragging]
[   0.016][v][cplayer] Run command: define-section, flags=0, args=[input_forced_osc, , force]
[   0.016][v][cplayer] Run command: enable-section, flags=0, args=[input_forced_osc, allow-hide-cursor+allow-vo-dragging]
[   0.016][v][cplayer] Done loading @osc.lua.
[   0.016][v][ytdl_hook] Loading script @ytdl_hook.lua...
[   0.017][v][global] config path: 'scripts' -/-> '/home/theking/.mpv/scripts'
[   0.017][v][global] config path: 'scripts' -/-> '/etc/mpv/scripts'
[   0.017][v][ytdl_hook] loading mp.defaults
[   0.018][v][cplayer] Run command: disable-section, flags=0, args=[input]
[   0.018][v][global] config path: 'fonts' -/-> '/home/theking/.mpv/fonts'
[   0.018][v][global] config path: 'fonts' -/-> '/etc/mpv/fonts'
[   0.018][v][osd/libass] Shaper: FriBidi 0.19.6 (SIMPLE) HarfBuzz-ng 0.9.27 (COMPLEX)
[   0.018][v][global] config path: 'subfont.ttf' -/-> '/home/theking/.mpv/subfont.ttf'
[   0.018][v][global] config path: 'subfont.ttf' -/-> '/etc/mpv/subfont.ttf'
[   0.018][v][global] config path: 'fonts.conf' -/-> '/home/theking/.mpv/fonts.conf'
[   0.018][v][global] config path: 'fonts.conf' -/-> '/etc/mpv/fonts.conf'
[   0.018][v][osd/libass] Setting up fonts...
[   0.019][v][ytdl_hook] loading @ytdl_hook.lua
[   0.021][v][cplayer] Run command: hook-add, flags=0, args=[on_load, 1, 10]
[   0.021][v][cplayer] Done loading @ytdl_hook.lua.
[   0.021][v][global] config path: 'scripts' -/-> '/home/theking/.mpv/scripts'
[   0.021][v][global] config path: 'scripts' -/-> '/etc/mpv/scripts'
[   0.021][v][global] config path: 'watch_later' -> '/home/theking/.mpv/watch_later'
[   0.021][i][cplayer] Playing: test.mkv
[   0.021][v][cplayer] Running hook: ytdl_hook/on_load
[   0.021][v][cplayer] Run command: hook-ack, flags=0, args=[on_load]
[   0.024][v][ifo] Opening test.mkv
[   0.025][v][ifo/dvdnav] Opening test.mkv
[   0.026][v][bdmv/bluray] Opening test.mkv
[   0.027][v][file] Opening test.mkv
[   0.027][e][file] Cannot open file 'test.mkv': No such file or directory
[   0.027][e][stream] Failed to open test.mkv.
[   0.028][v][cplayer] finished playback, loading failed (reason 4)
[   0.028][i][cplayer] 
[   0.028][i][cplayer] 
[   0.028][i][cplayer] Exiting... (Errors when loading file)
[   0.031][v][osd/libass] Using font provider fontconfig
[   0.031][v][osd/libass] Done.
[   0.033][v][ytdl_hook] Exiting...
[   0.035][v][osc] Exiting...
```

with .mkv plays but no sound
```
[   0.006][v][cplayer] Command line options: '--log-file=mpv.txt' '--v' 'test.mkv'[   0.006][v][cplayer] mpv git-bda1110 (C) 2000-2016 mpv/MPlayer/mplayer2 projects
[   0.006][v][cplayer]  built on Sat Apr 30 02:41:02 UTC 2016
[   0.006][v][cplayer] ffmpeg library versions:
[   0.006][v][cplayer]    libavutil       55.23.100
[   0.006][v][cplayer]    libavcodec      57.38.100
[   0.006][v][cplayer]    libavformat     57.34.103
[   0.006][v][cplayer]    libswscale      4.1.100
[   0.006][v][cplayer]    libavfilter     6.44.100
[   0.006][v][cplayer]    libswresample   2.0.101
[   0.006][v][cplayer] ffmpeg version: N-79691-g66dd21d
[   0.006][v][cplayer] 
[   0.007][v][cplayer] Configuration: ./waf configure --enable-pdf-build --prefix=/usr --confdir=/etc/mpv
[   0.007][v][cplayer] List of enabled features: alsa any-gl asm atomic-builtins atomics audio-input av-avpacket-int64-duration av-new-pixdesc av-pix-fmt-mmal av-subtitle-nopict av-version-info avcodec-chroma-pos-api avcodec-has-codecpar avcodec-new-codec-api avcodec-profile-name avframe-metadata avframe-skip-samples avutil-has-hwcontext build-date cdda cplayer debug-build dlopen drm dvbin dvdnav dvdread encoding fchmod gl gl-x11 glibc-thread-name glob iconv jack jpeg lcms2 libass libass-osd libav libavdevice libavfilter libbluray libdl libguess libm librt libsmbclient libswresample libv4l2 linux-fstatfs lua nanosleep optimize oss-audio oss-audio-native posix posix-or-mingw posix-spawn pthreads pulse resampler rubberband shm sse4-intrinsics standard-gl subprocess termios tv tv-v4l2 uchardet vaapi vaapi-glx vaapi-hwaccel vaapi-x11 vdpau vdpau-gl-x11 vdpau-hwaccel videodev vt.h x11 xext xinerama xrandr xss xv zlib
[   0.007][v][global] config path: '' -> '/home/theking/.mpv'
[   0.007][v][global] config path: 'mpv.conf' -/-> '/home/theking/.mpv/mpv.conf'
[   0.007][v][global] config path: 'config' -> '/home/theking/.mpv/config'
[   0.007][v][global] config path: 'mpv.conf' -/-> '/etc/mpv/mpv.conf'
[   0.007][v][global] config path: 'config' -/-> '/etc/mpv/config'
[   0.007][v][cplayer] Reading config file /home/theking/.mpv/config
[   0.007][v][cplayer] Setting option 'log-file' = 'mpv.txt' (flags = 8)
[   0.007][v][cplayer] Setting option 'v' = '' (flags = 8)
[   0.008][v][global] config path: 'input.conf' -/-> '/home/theking/.mpv/input.conf'
[   0.008][v][global] config path: 'input.conf' -/-> '/etc/mpv/input.conf'
[   0.008][v][input] Falling back on default (hardcoded) input config
[   0.008][v][osc] Loading script @osc.lua...
[   0.009][v][global] config path: 'scripts' -/-> '/home/theking/.mpv/scripts'
[   0.009][v][global] config path: 'scripts' -/-> '/etc/mpv/scripts'
[   0.009][v][osc] loading mp.defaults
[   0.011][v][osc] loading @osc.lua
[   0.016][v][global] config path: 'lua-settings/osc.conf' -/-> '/home/theking/.mpv/lua-settings/osc.conf'
[   0.016][v][global] config path: 'lua-settings/osc.conf' -/-> '/etc/mpv/lua-settings/osc.conf'
[   0.016][v][osc] lua-settings/osc.conf not found. 
[   0.017][v][cplayer] Run command: define-section, flags=0, args=[showhide, mouse_move script-binding osc/__keybinding1
[   0.017][v][cplayer] mouse_leave script-binding osc/__keybinding2
[   0.017][v][cplayer] , force]
[   0.017][v][cplayer] Run command: enable-section, flags=0, args=[showhide, allow-hide-cursor+allow-vo-dragging]
[   0.017][v][cplayer] Run command: define-section, flags=0, args=[input, mouse_btn0 script-binding osc/__keybinding3
[   0.017][v][cplayer] shift+mouse_btn0 script-binding osc/__keybinding4
[   0.017][v][cplayer] mouse_btn2 script-binding osc/__keybinding5
[   0.017][v][cplayer] mouse_btn0_dbl ignore
[   0.017][v][cplayer] shift+mouse_btn0_dbl ignore
[   0.017][v][cplayer] mouse_btn2_dbl ignore
[   0.017][v][cplayer] , force]
[   0.017][v][cplayer] Run command: enable-section, flags=0, args=[input, ]
[   0.017][v][cplayer] Run command: define-section, flags=0, args=[input_osc, del script-binding osc/__keybinding6
[   0.017][v][cplayer] , default]
[   0.017][v][cplayer] Run command: enable-section, flags=0, args=[input_osc, allow-hide-cursor+allow-vo-dragging]
[   0.017][v][cplayer] Run command: define-section, flags=0, args=[input_forced_osc, , force]
[   0.017][v][cplayer] Run command: enable-section, flags=0, args=[input_forced_osc, allow-hide-cursor+allow-vo-dragging]
[   0.017][v][cplayer] Done loading @osc.lua.
[   0.017][v][ytdl_hook] Loading script @ytdl_hook.lua...
[   0.018][v][global] config path: 'scripts' -/-> '/home/theking/.mpv/scripts'
[   0.018][v][global] config path: 'scripts' -/-> '/etc/mpv/scripts'
[   0.018][v][ytdl_hook] loading mp.defaults
[   0.019][v][cplayer] Run command: disable-section, flags=0, args=[input]
[   0.019][v][global] config path: 'fonts' -/-> '/home/theking/.mpv/fonts'
[   0.019][v][global] config path: 'fonts' -/-> '/etc/mpv/fonts'
[   0.019][v][osd/libass] Shaper: FriBidi 0.19.6 (SIMPLE) HarfBuzz-ng 0.9.27 (COMPLEX)
[   0.019][v][global] config path: 'subfont.ttf' -/-> '/home/theking/.mpv/subfont.ttf'
[   0.019][v][global] config path: 'subfont.ttf' -/-> '/etc/mpv/subfont.ttf'
[   0.019][v][global] config path: 'fonts.conf' -/-> '/home/theking/.mpv/fonts.conf'
[   0.019][v][global] config path: 'fonts.conf' -/-> '/etc/mpv/fonts.conf'
[   0.019][v][osd/libass] Setting up fonts...
[   0.019][v][ytdl_hook] loading @ytdl_hook.lua
[   0.020][v][cplayer] Run command: hook-add, flags=0, args=[on_load, 1, 10]
[   0.020][v][cplayer] Done loading @ytdl_hook.lua.
[   0.021][v][global] config path: 'scripts' -/-> '/home/theking/.mpv/scripts'
[   0.021][v][global] config path: 'scripts' -/-> '/etc/mpv/scripts'
[   0.021][v][global] config path: 'watch_later' -> '/home/theking/.mpv/watch_later'
[   0.021][i][cplayer] Playing: test.mkv
[   0.021][v][cplayer] Running hook: ytdl_hook/on_load
[   0.021][v][cplayer] Run command: hook-ack, flags=0, args=[on_load]
[   0.024][v][ifo] Opening test.mkv
[   0.025][v][ifo/dvdnav] Opening test.mkv
[   0.026][v][bdmv/bluray] Opening test.mkv
[   0.027][v][file] Opening test.mkv
[   0.027][v][file] Stream opened successfully.
[   0.027][v][demux] Trying demuxers for level=normal.
[   0.031][v][osd/libass] Using font provider fontconfig
[   0.031][v][osd/libass] Done.
[   0.058][v][mkv] Found the head...
[   0.058][v][mkv] + a segment...
[   0.058][v][mkv] Parsing seek head...
[   0.058][v][mkv] |+ segment information...
[   0.058][v][mkv] | + muxing app: libmkv 0.6.5.1
[   0.058][v][mkv] | + writing app: HandBrake rev5474
[   0.058][v][mkv] | + timecode scale: 1000000
[   0.058][v][mkv] | + duration: 8217.292s
[   0.058][v][mkv] | + segment uid 4d 74 00 d7 d4 f2 3e 74 7e 3c 28 c2 57 15 ef 49
[   0.058][v][mkv] |+ segment tracks...
[   0.058][v][mkv] | + a track...
[   0.058][v][mkv] |  + Track number: 1
[   0.058][v][mkv] |  + Track type: Video
[   0.058][v][mkv] |  + Video track
[   0.058][v][mkv] |   + Display width: 1920
[   0.058][v][mkv] |   + Display height: 800
[   0.058][v][mkv] |   + Pixel width: 1920
[   0.058][v][mkv] |   + Pixel height: 800
[   0.058][v][mkv] |  + Codec ID: V_MPEG4/ISO/AVC
[   0.058][v][mkv] |  + CodecPrivate, length 43
[   0.058][v][mkv] |  + Default flag: 1
[   0.058][v][mkv] |  + Default duration: 41.708ms ( = 23.976 fps)
[   0.058][v][mkv] | + a track...
[   0.058][v][mkv] |  + Track number: 2
[   0.058][v][mkv] |  + Track type: Audio
[   0.058][v][mkv] |  + Audio track
[   0.058][v][mkv] |   + Sampling frequency: 48000.000000
[   0.058][v][mkv] |   + Channels: 2
[   0.059][v][mkv] |  + Codec ID: A_AC3
[   0.059][v][mkv] |  + Language: eng
[   0.059][v][mkv] |  + Default flag: 1
[   0.059][v][mkv] |+ found cluster
[   0.059][v][mkv] Seeking to 2378765179 to read header element 0x114d9b74.
[   0.063][v][mkv] Parsing seek head...
[   0.064][v][mkv] Deferring reading cues.
[   0.064][v][mkv] Seeking to 2378794213 to read header element 0x1254c367.
[   0.064][v][mkv] All headers are parsed!
[   0.064][v][demux] Detected file format: Matroska
[   0.064][v][find_files] Loading external files in .
[   0.064][v][global] config path: 'sub/' -/-> '/home/theking/.mpv/sub/'
[   0.065][v][global] config path: 'sub/' -/-> '/etc/mpv/sub/'
[   0.065][v][global] config path: 'audio/' -/-> '/home/theking/.mpv/audio/'
[   0.065][v][global] config path: 'audio/' -/-> '/etc/mpv/audio/'
[   0.065][i][cplayer]  (+) Video --vid=1 (*) (h264)
[   0.065][i][cplayer]  (+) Audio --aid=1 --alang=eng (*) (ac3)
[   0.065][i][display-tags] File tags:
[   0.065][i][display-tags]  Title: The.Hunger.Games.Mockingjay.Part.2.2015.1080p.BluRay.x264.anoXmous
[   0.065][v][vo/opengl] Initializing OpenGL backend 'x11probe'
[   0.065][v][vo/opengl/x11] X11 opening display: :0
[   0.071][v][vo/opengl/x11] X11 running at 1366x768 (":0" => local display)
[   0.074][v][vo/opengl/x11] Detected wm supports NetWM.
[   0.074][v][vo/opengl/x11] Detected wm supports FULLSCREEN state.
[   0.074][v][vo/opengl/x11] Detected wm supports ABOVE state.
[   0.074][v][vo/opengl/x11] Detected wm supports BELOW state.
[   0.075][v][vo/opengl/x11] Display 0 (LVDS-1): [0, 0, 1366, 768] @ 60.046447 FPS
[   0.075][v][vo/opengl/x11] Current display FPS: 60.046447
[   0.181][v][vo/opengl] GLX chose FB config with ID 0xd82aa960
[   0.181][v][vo/opengl] GLX chose visual with ID 0x304
[   0.182][v][vo/opengl] Creating OpenGL 3.3 context...
[   0.184][v][vo/opengl] GL_VERSION='3.3 (Core Profile) Mesa 11.0.2'
[   0.184][v][vo/opengl] Detected desktop OpenGL 3.3.
[   0.184][v][vo/opengl] GL_VENDOR='nouveau'
[   0.184][v][vo/opengl] GL_RENDERER='Gallium 0.4 on NVA8'
[   0.184][v][vo/opengl] GL_SHADING_LANGUAGE_VERSION='3.30'
[   0.184][v][vo/opengl] Loaded functions for 210/builtin.
[   0.184][v][vo/opengl] Loaded functions for 210/builtin.
[   0.184][v][vo/opengl] Loaded functions for 300/builtin.
[   0.184][v][vo/opengl] Loaded functions for 210/builtin.
[   0.184][v][vo/opengl] Loaded functions for 110/GL_EXT_unpack_subimage.
[   0.185][v][vo/opengl] Loaded functions for 300/GL_ARB_framebuffer_object.
[   0.185][v][vo/opengl] Loaded functions for 300/GL_ARB_vertex_array_object.
[   0.185][v][vo/opengl] Loaded functions for 300/GL_ARB_texture_rg.
[   0.185][v][vo/opengl] Loaded functions for 300/GL_EXT_texture_norm16.
[   0.185][v][vo/opengl] Loaded functions for 320/GL_ARB_sync.
[   0.185][v][vo/opengl] Loaded functions for 0/GLX_SGI_swap_control.
[   0.185][v][vo/opengl] Loaded functions for 0/GLX_SGI_video_sync.
[   0.185][v][vo/opengl] Loaded functions for 0/GL_NV_vdpau_interop.
[   0.185][v][vo/opengl] Loaded functions for 430/GL_ARB_debug_output.
[   0.185][v][vo/opengl] Loaded functions for 310/GL_ARB_uniform_buffer_object.
[   0.185][v][vo/opengl] Filterable half-float textures supported.
[   0.185][v][vo/opengl] Reported display depth: R=8, G=8, B=8
[   0.186][v][vo/opengl] 16 bit texture depth: 16.
[   0.186][v][vo/opengl] Testing user-set FBO format (0x805b)
[   0.186][v][vo/opengl] Create FBO: 16x16 -> 16x16
[   0.186][v][vo/opengl] No advanced processing required. Enabling dumb mode.
[   0.186][v][vo/opengl] Assuming 60.046447 FPS for display sync.
[   0.186][v][vd] Container reported FPS: 23.976025
[   0.186][v][vd] Codec list:
[   0.186][v][vd]     lavc:h264 - H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10
[   0.186][v][vd] Opening video decoder lavc:h264
[   0.186][v][vd] Using software decoding.
[   0.187][v][vd] Detected 4 logical cores.
[   0.187][v][vd] Requesting 5 threads for decoding.
[   0.218][v][vd] Selected video codec: H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10 [lavc:h264]
[   0.219][v][vo/opengl/x11] Disabling screensaver.
[   0.222][v][ad] Codec list:
[   0.222][v][ad]     lavc:ac3 - ATSC A/52A (AC-3)
[   0.222][v][ad]     lavc:ac3_fixed (ac3) - ATSC A/52A (AC-3)
[   0.222][v][ad] Opening audio decoder lavc:ac3
[   0.223][v][ad] Requesting 1 threads for decoding.
[   0.234][v][ad] Selected audio codec: ATSC A/52A (AC-3) [lavc:ac3]
[   0.234][v][cplayer] Starting playback...
[   0.258][v][af] Audio filter chain:
[   0.258][v][af]   [in] 48000Hz stereo 2ch floatp
[   0.258][v][af]   [out] 48000Hz stereo 2ch floatp
[   0.258][v][af]   [ao] 48000Hz stereo 2ch floatp
[   0.258][v][ao] Trying audio driver 'pulse'
[   0.258][v][ao/pulse] requested format: 48000 Hz, stereo channels, floatp
[   0.261][v][ao/pulse] Library version: 4.0.0
[   0.261][v][ao/pulse] Proto: 28
[   0.261][v][ao/pulse] Server proto: 4294967295
[   0.262][v][ao/pulse] Channel layouts:
[   0.262][v][ao/pulse]  - #fl
[   0.262][v][ao/pulse]  - #fr
[   0.262][v][ao/pulse]  - #fc
[   0.262][v][ao/pulse]  - #lfe
[   0.262][v][ao/pulse]  - #bl
[   0.262][v][ao/pulse]  - #br
[   0.262][v][ao/pulse]  - #flc
[   0.263][v][ao/pulse]  - #frc
[   0.263][v][ao/pulse]  - #bc
[   0.263][v][ao/pulse]  - #sl
[   0.263][v][ao/pulse]  - #sr
[   0.263][v][ao/pulse]  - #tc
[   0.263][v][ao/pulse]  - #tfl
[   0.263][v][ao/pulse]  - #tfc
[   0.263][v][ao/pulse]  - #tfr
[   0.263][v][ao/pulse]  - #tbl
[   0.263][v][ao/pulse]  - #tbc
[   0.264][v][ao/pulse]  - #tbr
[   0.264][v][ao/pulse] result: stereo
[   0.489][v][ao/pulse] device buffer: 6000 samples.
[   0.490][v][ao/pulse] using soft-buffer of 9600 samples.
[   0.490][i][cplayer] AO: [pulse] 48000Hz stereo 2ch float
[   0.490][v][cplayer] AO: Description: PulseAudio audio output
[   0.490][v][af] Adding filter lavrresample 
[   0.490][v][af] Audio filter chain:
[   0.491][v][af]   [in] 48000Hz stereo 2ch floatp
[   0.491][v][af]   [lavrresample] 48000Hz stereo 2ch float
[   0.491][v][af]   [out] 48000Hz stereo 2ch float
[   0.491][v][af]   [ao] 48000Hz stereo 2ch float
[   0.555][v][vd] Decoder format: 1920x800 yuv420p bt.709/limited CL=mpeg2/4/h264
[   0.555][v][vd] Using container aspect ratio.
[   0.556][v][vf] Video filter chain:
[   0.556][v][vf]   [in] 1920x800 yuv420p bt.709/limited CL=mpeg2/4/h264
[   0.556][v][vf]   [out] 1920x800 yuv420p bt.709/limited CL=mpeg2/4/h264
[   0.557][i][cplayer] VO: [opengl] 1920x800 yuv420p
[   0.557][v][cplayer] VO: Description: Extended OpenGL Renderer
[   0.562][v][vo/opengl] Resize: 1362x714
[   0.562][v][vo/opengl] Window size: 1362x714
[   0.562][v][vo/opengl] Video source: 1920x800 (1:1)
[   0.562][v][vo/opengl] Video display: (0, 0) 1920x800 -> (0, 73) 1362x567
[   0.562][v][vo/opengl] Video scale: 0.709375/0.708750
[   0.562][v][vo/opengl] OSD borders: l=0 t=73 r=0 b=74
[   0.562][v][vo/opengl] Video borders: l=0 t=73 r=0 b=74
[   0.562][v][vo/opengl] Testing user-set FBO format (0x805b)
[   0.562][v][vo/opengl] Create FBO: 16x16 -> 16x16
[   0.565][v][vo/opengl] No advanced processing required. Enabling dumb mode.
[   0.567][v][vo/opengl] Texture for plane 0: 1920x800
[   0.568][v][vo/opengl] Texture for plane 1: 960x400
[   0.569][v][vo/opengl] Texture for plane 2: 960x400
[   0.569][v][vo/opengl] Reinit rendering.
[   0.569][v][cplayer] set video colors output-levels=0 
[   0.570][v][vo/opengl] Resize: 1366x744
[   0.570][v][vo/opengl] Window size: 1366x744
[   0.570][v][vo/opengl] Video source: 1920x800 (1:1)
[   0.570][v][vo/opengl] Video display: (0, 0) 1920x800 -> (0, 87) 1366x569
[   0.570][v][vo/opengl] Video scale: 0.711458/0.711250
[   0.570][v][vo/opengl] OSD borders: l=0 t=87 r=0 b=88
[   0.570][v][vo/opengl] Video borders: l=0 t=87 r=0 b=88
[   0.573][v][vo/opengl] recompiling a shader program:
[   0.573][v][vo/opengl] [  1] color.r = 1.000000 * vec4(texture(texture0, texcoord0)).r;
[   0.573][v][vo/opengl] [  2] color.g = 1.000000 * vec4(texture(texture1, texcoord1)).r;
[   0.573][v][vo/opengl] [  3] color.b = 1.000000 * vec4(texture(texture2, texcoord2)).r;
[   0.573][v][vo/opengl] [  4] // color conversion
[   0.573][v][vo/opengl] [  5] color.rgb = mat3(colormatrix) * color.rgb + colormatrix_c;
[   0.573][v][vo/opengl] [  6] color.a = 1.0;
[   0.573][v][vo/opengl] [  7] // color management
[   0.589][v][osd/libass] fontselect: (sans-serif, 400, 0) -> /usr/share/fonts/truetype/dejavu/DejaVuSans.ttf, 0, DejaVuSans
[   0.590][v][cplayer] first video frame after restart shown
[   0.590][v][cplayer] starting audio playback
[   0.590][v][cplayer] playback restart complete
[   3.973][v][cplayer] Run command: ignore, flags=9, args=[]
[   4.015][v][cplayer] Run command: ignore, flags=9, args=[]
[   4.056][v][cplayer] Run command: ignore, flags=9, args=[]
[   4.098][v][cplayer] Run command: ignore, flags=9, args=[]
[   4.140][v][cplayer] Run command: ignore, flags=9, args=[]
[   4.181][v][cplayer] Run command: ignore, flags=9, args=[]
[   4.223][v][cplayer] Run command: ignore, flags=9, args=[]
[   4.265][v][cplayer] Run command: ignore, flags=9, args=[]
[   4.307][v][cplayer] Run command: ignore, flags=9, args=[]
[   4.348][v][cplayer] Run command: ignore, flags=9, args=[]
[   4.390][v][cplayer] Run command: ignore, flags=9, args=[]
[   4.432][v][cplayer] Run command: ignore, flags=9, args=[]
[   4.473][v][cplayer] Run command: ignore, flags=9, args=[]
[   4.473][v][cplayer] Run command: script-binding, flags=9, args=[osc/__keybinding2]
[   4.515][v][cplayer] Run command: ignore, flags=9, args=[]
[   4.557][v][cplayer] Run command: ignore, flags=9, args=[]
[   4.599][v][cplayer] Run command: ignore, flags=9, args=[]
[   4.640][v][cplayer] Run command: ignore, flags=9, args=[]
[   4.682][v][cplayer] Run command: ignore, flags=9, args=[]
[   4.724][v][cplayer] Run command: ignore, flags=9, args=[]
[   4.765][v][cplayer] Run command: ignore, flags=9, args=[]
[   4.807][v][cplayer] Run command: ignore, flags=9, args=[]
[   4.849][v][cplayer] Run command: ignore, flags=9, args=[]
[   4.890][v][cplayer] Run command: script-binding, flags=9, args=[osc/__keybinding2]
[  11.689][v][vo/opengl] Resize: 1362x714
[  11.689][v][vo/opengl] Window size: 1362x714
[  11.689][v][vo/opengl] Video source: 1920x800 (1:1)
[  11.689][v][vo/opengl] Video display: (0, 0) 1920x800 -> (0, 73) 1362x567
[  11.689][v][vo/opengl] Video scale: 0.709375/0.708750
[  11.689][v][vo/opengl] OSD borders: l=0 t=73 r=0 b=74
[  11.689][v][vo/opengl] Video borders: l=0 t=73 r=0 b=74
[  12.397][v][cplayer] Run command: ignore, flags=9, args=[]
[  12.440][v][cplayer] Run command: ignore, flags=9, args=[]
[  12.480][v][cplayer] Run command: ignore, flags=9, args=[]
[  12.522][v][cplayer] Run command: script-binding, flags=9, args=[osc/__keybinding2]
[  14.899][v][cplayer] Run command: quit, flags=9, args=[0]
[  14.899][v][cplayer] EOF code: 6  
[  14.903][v][ad] Uninit audio decoder.
[  14.903][v][af] Removing filter lavrresample 
[  14.904][v][vd] Uninit video.
[  14.906][v][cplayer] finished playback, success (reason 3)
[  14.906][i][cplayer] 
[  14.906][i][cplayer] 
[  14.907][i][cplayer] Exiting... (Quit)
[  14.910][v][ytdl_hook] Exiting...
[  14.911][v][osc] Exiting...
[  14.911][v][ao/pulse] draining...
[  14.916][v][vo/opengl/x11] Enabling screensaver.
[  14.916][v][vo/opengl/x11] uninit ...
```


Here's the BASH output from mplayer playing an .mp3 - plays, but no sound.

```
Creating config file: /home/theking/.mplayer/configMPlayer 1.1-4.8 (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.


Playing Introduction.mp3.
libavformat version 54.20.4 (external)
Mismatching header version 54.20.3
Audio only file format detected.
Clip info:
 Title: Introduction                  
 Artist: Blutengel                     
 Album: Child of glass                
 Year: 1999
 Comment:                             
 Track: 1
 Genre: Other
Load subtitles in ./
==========================================================================
Requested audio codec family [mpg123] (afm=mpg123) not available.
Enable it at compilation.
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
libavcodec version 54.35.0 (external)
AUDIO: 44100 Hz, 2 ch, floatle, 320.1 kbit/11.34% (ratio: 40013->352800)
Selected audio codec: [ffmp3float] afm: ffmpeg (FFmpeg MPEG layer-3 audio)
==========================================================================
AO: [pulse] 44100Hz 2ch floatle (4 bytes per sample)
Video: no video
Starting playback...
A:  18.7 (18.7) of 76.0 (01:16.0)  0.6% 


Exiting... (Quit)



```

I've already tested my soundcard and it appears to be working. I can play .wav files with sound.

---

### Post by Bucky Ball on 2016-05-06
Have you tried installing ubuntu-restricted-extras? You should be able to find it in your package manager.

---

### Post by peter228 on 2016-05-06
What happens if you use vlc as the player?

---

### Post by jeff162 on 2016-05-06
> 
[LIST]
[*][INDENT]What happens if you use vlc as the player?[/INDENT]
[/LIST]


I get the same results

> 
[LIST]
[*][INDENT]Have you tried installing ubuntu-restricted-extras? You should be able to find it in your package manager.[/INDENT]
[/LIST]


It was already installed.

---

### Post by mc4man on 2016-05-07
If inclined stick one of those doesn't play at all .mp4's here, provide link
[http://www.datafilehost.com/](http://www.datafilehost.com/)

---

### Post by jeff162 on 2016-05-09
> **mc4man said:**
> If inclined stick one of those doesn't play at all .mp4's here, provide link
[http://www.datafilehost.com/](http://www.datafilehost.com/)

As it turns out the .mp4's that don't play at all are corrupted. I tried them on a friends PC over the weekend. I got some more with youtube-dl that play and I'll send one of those to see if it might be helpful. All the formats I've tried including the youtube .mp4's still have no sound. 

[https://www.datafilehost.com/d/4822d094](https://www.datafilehost.com/d/4822d094)

---

### Post by CantankRus on 2016-05-09
FYI file plays here on Xenial.
Output from mplayer....
```
[COLOR="#006400"]glen@Xenial:~$[/COLOR] **mplayer "/home/glen/Downloads/Bruce Springsteen opens Brooklyn show with Purple Rain.mp4"**
MPlayer 1.2.1 (Debian), built with gcc-5.3.1 (C) 2000-2016 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/glen/Downloads/Bruce Springsteen opens Brooklyn show with Purple Rain.mp4.
libavformat version 56.40.101 (external)
libavformat file format detected.
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x7f08059c2e00]Protocol name not provided, cannot determine if input is local or a network protocol, buffers and access patterns cannot be configured optimally without knowing the protocol
[lavf] stream 0: video (h264), -vid 0
[lavf] stream 1: audio (aac), -aid 0, -alang und
VIDEO:  [H264]  568x320  24bpp  29.970 fps  333.3 kbps (40.7 kbyte/s)
Clip info:
 major_brand: mp42
 minor_version: 0
 compatible_brands: isommp42
 creation_time: 2016-04-24 07:04:24
Load subtitles in /home/glen/Downloads/
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
libavcodec version 56.60.100 (external)
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
[B]Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, floatle, 96.0 kbit/3.40% (ratio: 12000->352800)
Selected audio codec: [ffaac] afm: ffmpeg (FFmpeg AAC (MPEG-2/MPEG-4 Audio))[/B]
==========================================================================
AO: [pulse] 44100Hz 2ch floatle (4 bytes per sample)
Starting playback...
Movie-Aspect is 1.77:1 - prescaling to correct movie aspect.
VO: [vdpau] 568x320 => 568x320 Planar YV12 
A:  11.2 V:  11.2 A-V:  0.000 ct:  0.033   0/  0  4%  1%  0.3% 0 0
```

Try using mplayer for more info. May need to install.
Once installed, in terminal run...
```
mplayer "[COLOR="#808080"]/path/to/file[/COLOR]"
```

---

### Post by jeff162 on 2016-05-12
Sorry for the delay, life took over for a few days. 

Here are the outputs of mplayer.  I flagged the option to be verbose.


.mp4, plays, no sound

```
MPlayer 1.1-4.8 (C) 2000-2012 MPlayer TeamCPU vendor name: GenuineIntel  max cpuid level: 11
CPU: Intel(R) Core(TM) i5 CPU       M 430  @ 2.27GHz (Family: 6, Model: 37, Stepping: 2)
extended cpuid-level: 8
extended cache-info: 16801856
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNowExt: 0 SSE: 1 SSE2: 1 SSSE3: 1
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/theking/.mplayer/codecs.conf'
Reading optional codecs config file /home/theking/.mplayer/codecs.conf: No such file or directory
Reading optional codecs config file /etc/mplayer/codecs.conf: No such file or directory
Using built-in default codecs.conf.
init_freetype
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/theking/.mplayer/fonts'
Configuration: --prefix=/usr --confdir=/etc/mplayer --enable-xvmc --enable-menu --enable-radio --enable-radio-capture --disable-arts --language=all --disable-dvdread-internal --disable-libdvdcss-internal --disable-libmpeg2-internal --disable-ffmpeg_a --enable-runtime-cpudetection --enable-debug --enable-joystick --disable-gui
CommandLine: '-v' 'testshort.mp4'
Using nanosleep() timing
get_path('input.conf') -> '/home/theking/.mplayer/input.conf'
Reading optional input config file /home/theking/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 92 binds
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
get_path('testshort.mp4.conf') -> '/home/theking/.mplayer/testshort.mp4.conf'


Playing testshort.mp4.
get_path('sub/') -> '/home/theking/.mplayer/sub/'
[file] File size is 19958688 bytes
STREAM: [file] testshort.mp4
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
libavformat version 54.20.4 (external)
Mismatching header version 54.20.3
Configuration: --arch=amd64 --enable-pthreads --enable-runtime-cpudetect --extra-version='6:9.18-0ubuntu0.14.04.1' --libdir=/usr/lib/x86_64-linux-gnu --prefix=/usr --enable-bzlib --enable-libdc1394 --enable-libfreetype --enable-frei0r --enable-gnutls --enable-libgsm --enable-libmp3lame --enable-librtmp --enable-libopenjpeg --enable-libopus --enable-libpulse --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-vaapi --enable-vdpau --enable-libvorbis --enable-libvpx --enable-zlib --enable-gpl --enable-swscale --enable-libcdio --enable-x11grab --enable-libx264 --enable-libxvid --shlibdir=/usr/lib/x86_64-linux-gnu --enable-shared --disable-static
LAVF_check: QuickTime / MOV
libavformat file format detected.
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x7f9df0d0b600]ISO: File Type Major Brand: mp42
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x7f9df0d0b600]All info found
==> Found video stream: 0
======= VIDEO Format ======
  biSize 78
  biWidth 568
  biHeight 320
  biPlanes 0
  biBitCount 24
  biCompression 875967048='H264'
  biSizeImage 545280
Unknown extra header dump: [1] [42] [c0] [1e] [ff] [e1] [0] [17] [67] [42] [c0] [1e] [da] [2] [40] [a7] [97] [c0] [44] [0] [0] [f] [a4] [0] [3] [a9] [80] [3c] [58] [ba] [80] [1] [0] [4] [68] [ce] [3c] [80] 
===========================
[lavf] stream 0: video (h264), -vid 0
==> Found audio stream: 1
======= WAVE Format =======
Format Tag: 20557 (0x504D)
Channels: 2
Samplerate: 44100
avg byte/sec: 12000
Block align: 1
bits/sample: 16
cbSize: 16
Unknown extra header dump: [12] [10] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] 
==========================================================================
[lavf] stream 1: audio (aac), -aid 0, -alang und
LAVF: 1 audio and 1 video streams found
LAVF: build 3544067
VIDEO:  [H264]  568x320  24bpp  29.970 fps  333.3 kbps (40.7 kbyte/s)
[V] filefmt:44  fourcc:0x34363248  size:568x320  fps:29.970  ftime:=0.0334
Clip info:
 major_brand: mp42
 minor_version: 0
 compatible_brands: isommp42
 creation_time: 2016-04-24 07:04:24
Load subtitles in ./
get_path('sub/') -> '/home/theking/.mplayer/sub/'
X11 opening display: :0
vo: X11 color mask:  FFFFFF  (R:FF0000 G:FF00 B:FF)
vo: X11 running at 1366x768 with depth 24 and 32 bpp (":0" => local display)
[x11] Detected wm supports NetWM.
[x11] Detected wm supports FULLSCREEN state.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms
Disabling DPMS
DPMSDisable stat: 1
Failed to open VDPAU backend libvdpau_nouveau.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
[VO_XV] Using Xv Adapter #0 (Nouveau GeForce 8/9 Textured Video)
[xv common] Drawing no colorkey.
[xv common] Maximum source image dimensions: 8192x8192
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
libavcodec version 54.35.0 (external)
Configuration: --arch=amd64 --enable-pthreads --enable-runtime-cpudetect --extra-version='6:9.18-0ubuntu0.14.04.1' --libdir=/usr/lib/x86_64-linux-gnu --prefix=/usr --enable-bzlib --enable-libdc1394 --enable-libfreetype --enable-frei0r --enable-gnutls --enable-libgsm --enable-libmp3lame --enable-librtmp --enable-libopenjpeg --enable-libopus --enable-libpulse --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-vaapi --enable-vdpau --enable-libvorbis --enable-libvpx --enable-zlib --enable-gpl --enable-swscale --enable-libcdio --enable-x11grab --enable-libx264 --enable-libxvid --shlibdir=/usr/lib/x86_64-linux-gnu --enable-shared --disable-static
INFO: libavcodec init OK!
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
dec_audio: Allocating 1536000 + 131072 = 1667072 bytes for output buffer.
FFmpeg's libavcodec audio codec
INFO: libavcodec "aac" init OK!
AUDIO: 44100 Hz, 2 ch, floatle, 96.0 kbit/3.40% (ratio: 12000->352800)
Selected audio codec: [ffaac] afm: ffmpeg (FFmpeg AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
Building audio filter chain for 44100Hz/2ch/floatle -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 44100Hz/2ch/floatle
[dummy] Was reinitialized: 44100Hz/2ch/floatle
Trying preferred audio driver 'pulse', options '[none]'
AO: [pulse] 44100Hz 2ch floatle (4 bytes per sample)
AO: Description: PulseAudio audio output
AO: Author: Lennart Poettering
Building audio filter chain for 44100Hz/2ch/floatle -> 44100Hz/2ch/floatle...
[dummy] Was reinitialized: 44100Hz/2ch/floatle
[dummy] Was reinitialized: 44100Hz/2ch/floatle
Starting playback...
Increasing filtered audio buffer size from 0 to 92288
Unsupported AVPixelFormat 53
[ffmpeg] aspect_ratio: 1.775000
VDec: vo config request - 568 x 320 (preferred colorspace: Planar YV12)
Trying filter chain: vo
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.77:1 - prescaling to correct movie aspect.
VO Config (568x320->568x320,flags=0,'MPlayer',0x32315659)
VO: [xv] 568x320 => 568x320 Planar YV12 
VO: Description: X11/Xv
VO: Author: Gerd Knorr <kraxel@goldbach.in-berlin.de> and others
Xvideo image format: 0x32315659 (YV12) planar
Xvideo image format: 0x30323449 (I420) planar
Xvideo image format: 0x32595559 (YUY2) packed
Xvideo image format: 0x59565955 (UYVY) packed
using Xvideo port 63 for hw scaling
*** [vo] Exporting mp_image_t, 568x320x12bpp YUV planar, 272640 bytes
Unicode font: 5361 glyphs.
Unicode font: 5361 glyphs.
A:  11.7 V:  11.7 A-V:  0.000 ct:  0.033   0/  0  4%  1%  0.8% 0 0 
Uninit audio filters...
[libaf] Removing filter dummy 
Uninit audio: ffmpeg
Uninit video: ffmpeg
Successfully enabled DPMS
vo: uninit ...


Exiting... (Quit)



```

.mkv file, plays, no sound

```
MPlayer 1.1-4.8 (C) 2000-2012 MPlayer Teammplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.


Playing test.mkv.
libavformat version 54.20.4 (external)
Mismatching header version 54.20.3
libavformat file format detected.
[lavf] stream 0: video (h264), -vid 0
[lavf] stream 1: audio (ac3), -aid 0, -alang eng
VIDEO:  [H264]  1920x800  0bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 TITLE: The.Hunger.Games.Mockingjay.Part.2.2015.1080p.BluRay.x264.anoXmous
Load subtitles in ./
Failed to open VDPAU backend libvdpau_nouveau.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
libavcodec version 54.35.0 (external)
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, floatle, 160.0 kbit/5.21% (ratio: 20000->384000)
Selected audio codec: [ffac3] afm: ffmpeg (FFmpeg AC-3)
==========================================================================
AO: [pulse] 48000Hz 2ch floatle (4 bytes per sample)
Starting playback...
Unsupported AVPixelFormat 53
Movie-Aspect is 2.40:1 - prescaling to correct movie aspect.
VO: [xv] 1920x800 => 1920x800 Planar YV12 
A: 239.8 V: 239.8 A-V:  0.000 ct:  0.162   0/  0 22%  2%  0.6% 0 0 


Exiting... (Quit)



```

.avi, plays, no sound. This is all I got from mplayer. I didn't use the -v flag. A lot of information came out and all the info in the beginning was lost.

```
MPlayer 1.1-4.8 (C) 2000-2012 MPlayer Teammplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.


Playing avitest.avi.
libavformat version 54.20.4 (external)
Mismatching header version 54.20.3
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [MJPG]  640x480  24bpp  30.000 fps  10620.6 kbps (1296.5 kbyte/s)
Clip info:
 Digitization Time: Thu Dec 20 09:20:57 2007


 Software: CanonMVI06
Load subtitles in ./
Failed to open VDPAU backend libvdpau_nouveau.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
libavcodec version 54.35.0 (external)
Selected video codec: [ffmjpeg] vfm: ffmpeg (FFmpeg MJPEG)
==========================================================================
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 1411.2 kbit/100.00% (ratio: 176400->176400)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
Movie-Aspect is undefined - no prescaling applied.
[swscaler @ 0x7fc59293f640]using unscaled yuv422p -> yuyv422 special converter
VO: [xv] 640x480 => 640x480 Packed YUY2 
A:   8.0 V:   8.0 A-V:  0.000 ct:  0.000 241/241 12%  1%  0.1% 0 0 


Exiting... (Quit)



```

Finally, an .mp3 file. Plays, but no sound.

```
MPlayer 1.1-4.8 (C) 2000-2012 MPlayer TeamCPU vendor name: GenuineIntel  max cpuid level: 11
CPU: Intel(R) Core(TM) i5 CPU       M 430  @ 2.27GHz (Family: 6, Model: 37, Stepping: 2)
extended cpuid-level: 8
extended cache-info: 16801856
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNowExt: 0 SSE: 1 SSE2: 1 SSSE3: 1
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/theking/.mplayer/codecs.conf'
Reading optional codecs config file /home/theking/.mplayer/codecs.conf: No such file or directory
Reading optional codecs config file /etc/mplayer/codecs.conf: No such file or directory
Using built-in default codecs.conf.
init_freetype
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/theking/.mplayer/fonts'
Configuration: --prefix=/usr --confdir=/etc/mplayer --enable-xvmc --enable-menu --enable-radio --enable-radio-capture --disable-arts --language=all --disable-dvdread-internal --disable-libdvdcss-internal --disable-libmpeg2-internal --disable-ffmpeg_a --enable-runtime-cpudetection --enable-debug --enable-joystick --disable-gui
CommandLine: '-v' 'Introduction.mp3'
Using nanosleep() timing
get_path('input.conf') -> '/home/theking/.mplayer/input.conf'
Reading optional input config file /home/theking/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 92 binds
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
get_path('Introduction.mp3.conf') -> '/home/theking/.mplayer/Introduction.mp3.conf'


Playing Introduction.mp3.
get_path('sub/') -> '/home/theking/.mplayer/sub/'
[file] File size is 3080465 bytes
STREAM: [file] Introduction.mp3
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
libavformat version 54.20.4 (external)
Mismatching header version 54.20.3
Configuration: --arch=amd64 --enable-pthreads --enable-runtime-cpudetect --extra-version='6:9.18-0ubuntu0.14.04.1' --libdir=/usr/lib/x86_64-linux-gnu --prefix=/usr --enable-bzlib --enable-libdc1394 --enable-libfreetype --enable-frei0r --enable-gnutls --enable-libgsm --enable-libmp3lame --enable-librtmp --enable-libopenjpeg --enable-libopus --enable-libpulse --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-vaapi --enable-vdpau --enable-libvorbis --enable-libvpx --enable-zlib --enable-gpl --enable-swscale --enable-libcdio --enable-x11grab --enable-libx264 --enable-libxvid --shlibdir=/usr/lib/x86_64-linux-gnu --enable-shared --disable-static
LAVF_check: MP2/3 (MPEG audio layer 2/3)
Checking for YUV4MPEG2
ASF_check: not ASF guid!
Checking for REAL
Checking for SMJPEG
Searching demuxer type for filename Introduction.mp3 ext: .mp3
Trying demuxer 17 based on filename extension
==> Found audio stream: 0
demux_audio: seeking from 0x2F008B to start pos 0x400
demux_audio: audio data 0x400 - 0x2F0091  
Audio only file format detected.
Clip info:
 Title: Introduction                  
 Artist: Blutengel                     
 Album: Child of glass                
 Year: 1999
 Comment:                             
 Track: 1
 Genre: Other
Load subtitles in ./
get_path('sub/') -> '/home/theking/.mplayer/sub/'
==========================================================================
Requested audio codec family [mpg123] (afm=mpg123) not available.
Enable it at compilation.
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
dec_audio: Allocating 1536000 + 131072 = 1667072 bytes for output buffer.
FFmpeg's libavcodec audio codec
libavcodec version 54.35.0 (external)
Configuration: --arch=amd64 --enable-pthreads --enable-runtime-cpudetect --extra-version='6:9.18-0ubuntu0.14.04.1' --libdir=/usr/lib/x86_64-linux-gnu --prefix=/usr --enable-bzlib --enable-libdc1394 --enable-libfreetype --enable-frei0r --enable-gnutls --enable-libgsm --enable-libmp3lame --enable-librtmp --enable-libopenjpeg --enable-libopus --enable-libpulse --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-vaapi --enable-vdpau --enable-libvorbis --enable-libvpx --enable-zlib --enable-gpl --enable-swscale --enable-libcdio --enable-x11grab --enable-libx264 --enable-libxvid --shlibdir=/usr/lib/x86_64-linux-gnu --enable-shared --disable-static
INFO: libavcodec "mp3float" init OK!
AUDIO: 44100 Hz, 2 ch, floatle, 320.1 kbit/11.34% (ratio: 40013->352800)
Selected audio codec: [ffmp3float] afm: ffmpeg (FFmpeg MPEG layer-3 audio)
==========================================================================
Building audio filter chain for 44100Hz/2ch/floatle -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 44100Hz/2ch/floatle
[dummy] Was reinitialized: 44100Hz/2ch/floatle
Trying preferred audio driver 'pulse', options '[none]'
AO: [pulse] 44100Hz 2ch floatle (4 bytes per sample)
AO: Description: PulseAudio audio output
AO: Author: Lennart Poettering
Building audio filter chain for 44100Hz/2ch/floatle -> 44100Hz/2ch/floatle...
[dummy] Was reinitialized: 44100Hz/2ch/floatle
[dummy] Was reinitialized: 44100Hz/2ch/floatle
Video: no video
Freeing 0 unused video chunks.
Starting playback...
Increasing filtered audio buffer size from 0 to 92288
A:   9.7 (09.7) of 76.0 (01:16.0)  0.6% 
Uninit audio filters...
[libaf] Removing filter dummy 
Uninit audio: ffmpeg
vo: x11 uninit called but X11 not initialized..


Exiting... (Quit)



```

If there's any other info I can provide, let me know.

---

### Post by jeff162 on 2016-05-14
bump. Still having the problem

---

