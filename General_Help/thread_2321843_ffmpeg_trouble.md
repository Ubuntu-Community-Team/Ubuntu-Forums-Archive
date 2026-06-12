---
title: "ffmpeg trouble"
date: 2016-04-24
forum: General Help
---

### Post by jeff162 on 2016-04-24
I can't get sound from videos. Videos in Chrome work fine, but they crash firefox. I also get no sound if I play a file in mpv or vlc. I'm assuming ffmpeg is to blame but I can't reinstall it. The box for it has been grayed out in the Software Updater for several days and I can't reinstall ffmpeg from the software center. When I try, I get a dependency conflict.

I'm on Ubuntu 14.04

---

### Post by jeff162 on 2016-04-25
bump

---

### Post by mc4man on 2016-04-25
Run mpv from a terminal as such for several seconds, then quit (q on keyboard).
You can attach the .txt file to a post, it'll be in your home folder. Try to not use/move your cursor inside the video window as it will spam the log with useless info.

mpv --log-file=mpv.txt --v /path/to/file

---

### Post by jeff162 on 2016-04-26
Unfortunately I can't install mpv. I fet the following error:

```
Some packages could not be installed. This may mean that you haverequested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 mpv : Depends: libavfilter3 (>= 6:9.1-1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.



```

Additionally wben I try to open a video in any player I get a "could not determine type of stream" message.



Here's the BASH output from VLC when I try to open an .mp4 if it helps:

```
VLC media player 2.1.6 Rincewind (revision 2.1.6-0-gea01d28)[0x10dc118] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x7f6fc0009c98] mpgatofixed32 audio converter error: libmad error: forbidden bit allocation value
[0x7f6fc0009c98] mpgatofixed32 audio converter error: libmad error: input buffer too small (or EOF)



```






> **mc4man said:**
> Run mpv from a terminal as such for several seconds, then quit (q on keyboard).
You can attach the .txt file to a post, it'll be in your home folder. Try to not use/move your cursor inside the video window as it will spam the log with useless info.

mpv --log-file=mpv.txt --v /path/to/file

---

### Post by mc4man on 2016-04-26
That vlc error doesn't lead me anywhere. The mpv your trying to install is very, very old so not really worth using anyway.
However the error shouldn't be happening & that may be at the root of your issues.
What's this return - 
```
apt-cache policy libavfilter3 libavcodec54
```

---

### Post by jeff162 on 2016-04-26
Here it is:

```
libavfilter3:  Installed: (none)
  Candidate: 7:1.2.5-1~trusty1
  Version table:
     7:1.2.5-1~trusty1 0
        500 http://ppa.launchpad.net/noobslab/deepin-sc/ubuntu/ trusty/main amd64 Packages
     6:9.18-0ubuntu0.14.04.1+fdkaac 0
        500 http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/ trusty/main amd64 Packages
     6:9.18-0ubuntu0.14.04.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/universe amd64 Packages
     6:9.11-2ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
libavcodec54:
  Installed: 6:9.18-0ubuntu0.14.04.1
  Candidate: 7:1.2.5-1~trusty1
  Version table:
     7:1.2.5-1~trusty1 0
        500 http://ppa.launchpad.net/noobslab/deepin-sc/ubuntu/ trusty/main amd64 Packages
     6:9.18-0ubuntu0.14.04.1+fdkaac 0
        500 http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/ trusty/main amd64 Packages
 *** 6:9.18-0ubuntu0.14.04.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/universe amd64 Packages
        100 /var/lib/dpkg/status
     6:9.11-2ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages



```

---

### Post by mc4man on 2016-04-26
> libavfilter3:  Installed: (none)
  Candidate: 7:1.2.5-1~trusty1
  Version table:
     7:1.2.5-1~trusty1 0
        500 [http://ppa.launchpad.net/noobslab/deepin-sc/ubuntu/](http://ppa.launchpad.net/noobslab/deepin-sc/ubuntu/) trusty/main amd64 Packages
That's going to be a problem, you should disable that ppa, hopefully you haven't added any libav or ffmpeg shared lib packages from that ppa
(- if you install synaptic you can open synaptic > click on Origin in left sidebar & see what you installed from that nogoodslab ppa

If you want an mpv that will work then get from here (you have to add & use the ppa
[https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests](https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests)

---

### Post by jeff162 on 2016-04-28
Before I went to remove the deepin PPA I found it had installed several ffmpeg packages:

[http://imgur.com/AhuUQgT](http://imgur.com/AhuUQgT)

So I'm not sure what to do from here. I haven't removed the PPA yet.

---

### Post by mc4man on 2016-04-28
As far as that deepin ppa - I don't think any ffmpeg libs have been installed as they can't be. They have a dependency of libx264-123 which doesn't exist in the ppa nor in trusty repos.
So i'd just disable or remove the ppa, then update your sources. As far as the other non media packages from the ppa, you can keep them or remove them if not using.

Overall you seem to not be up to date in general. I see you have one of my ppa's enabled (trusty-media) but have not upgraded to it's packages, either fully or at all. If the later then also disable that ppa if not intending to use. If the former & again you don't want to use the ppa then you should use ppa-purge on it.
If you want to use the ppa then you need to fully upgrade (dist-upgrade) but [read page first!]("https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media")

Due to your unknown state if deciding to get upgraded fully I'd simulate first to check, ie.
sudo apt-get update
sudo apt-get -s dist-upgrade

---

### Post by jeff162 on 2016-04-28
> **mc4man said:**
> As far as that deepin ppa - I don't think any ffmpeg libs have been installed as they can't be. They have a dependency of libx264-123 which doesn't exist in the ppa nor in trusty repos.
So i'd just disable or remove the ppa, then update your sources. As far as the other non media packages from the ppa, you can keep them or remove them if not using.

Overall you seem to not be up to date in general. I see you have one of my ppa's enabled (trusty-media) but have not upgraded to it's packages, either fully or at all. If the later then also disable that ppa if not intending to use. If the former & again you don't want to use the ppa then you should use ppa-purge on it.
If you want to use the ppa then you need to fully upgrade (dist-upgrade) but [read page first!]("https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media")

Due to your unknown state if deciding to get upgraded fully I'd simulate first to check, ie.
sudo apt-get update
sudo apt-get -s dist-upgrade

I purged the deepin-sc and and trusty-media PPAs and still can't play videos. The updated version of mpv just hung with a caret (>) when I tried to play a vid. Is there a way to revert to all the packages I had before I started mucking around with PPAs? 

I appreciate all the handholding, by the way. I'm pretty lost here.

---

### Post by mc4man on 2016-04-28
> **jeff162 said:**
> I purged the deepin-sc and and trusty-media PPAs and still can't play videos. The updated version of mpv just hung with a caret (>) when I tried to play a vid.
That typically means an incomplete or improper command. Please post complete terminal output inc. command used. Or do as suggested in post 3

---

### Post by jeff162 on 2016-05-02
> **mc4man said:**
> That typically means an incomplete or improper command. Please post complete terminal output inc. command used. Or do as suggested in post 3

Here's the output of mpv from your PPA:

```

[   0.053][v][cplayer] Command line options: '--log-file=mpv.txt' '--v' 'test.mp4'
[   0.053][v][cplayer] mpv git-bda1110 (C) 2000-2016 mpv/MPlayer/mplayer2 projects
[   0.053][v][cplayer]  built on Sat Apr 30 02:41:02 UTC 2016
[   0.053][v][cplayer] ffmpeg library versions:
[   0.053][v][cplayer]    libavutil       55.23.100
[   0.053][v][cplayer]    libavcodec      57.38.100
[   0.053][v][cplayer]    libavformat     57.34.103
[   0.053][v][cplayer]    libswscale      4.1.100
[   0.053][v][cplayer]    libavfilter     6.44.100
[   0.053][v][cplayer]    libswresample   2.0.101
[   0.053][v][cplayer] ffmpeg version: N-79691-g66dd21d
[   0.053][v][cplayer] 
[   0.053][v][cplayer] Configuration: ./waf configure --enable-pdf-build --prefix=/usr --confdir=/etc/mpv
[   0.053][v][cplayer] List of enabled features: alsa any-gl asm atomic-builtins atomics audio-input av-avpacket-int64-duration av-new-pixdesc av-pix-fmt-mmal av-subtitle-nopict av-version-info avcodec-chroma-pos-api avcodec-has-codecpar avcodec-new-codec-api avcodec-profile-name avframe-metadata avframe-skip-samples avutil-has-hwcontext build-date cdda cplayer debug-build dlopen drm dvbin dvdnav dvdread encoding fchmod gl gl-x11 glibc-thread-name glob iconv jack jpeg lcms2 libass libass-osd libav libavdevice libavfilter libbluray libdl libguess libm librt libsmbclient libswresample libv4l2 linux-fstatfs lua nanosleep optimize oss-audio oss-audio-native posix posix-or-mingw posix-spawn pthreads pulse resampler rubberband shm sse4-intrinsics standard-gl subprocess termios tv tv-v4l2 uchardet vaapi vaapi-glx vaapi-hwaccel vaapi-x11 vdpau vdpau-gl-x11 vdpau-hwaccel videodev vt.h x11 xext xinerama xrandr xss xv zlib
[   0.053][v][global] config path: '' -> '/home/theking/.mpv'
[   0.053][v][global] config path: 'mpv.conf' -/-> '/home/theking/.mpv/mpv.conf'
[   0.053][v][global] config path: 'config' -> '/home/theking/.mpv/config'
[   0.053][v][global] config path: 'mpv.conf' -/-> '/etc/mpv/mpv.conf'
[   0.053][v][global] config path: 'config' -/-> '/etc/mpv/config'
[   0.053][v][cplayer] Reading config file /home/theking/.mpv/config
[   0.053][v][cplayer] Setting option 'log-file' = 'mpv.txt' (flags = 8)
[   0.053][v][cplayer] Setting option 'v' = '' (flags = 8)
[   0.055][v][global] config path: 'input.conf' -/-> '/home/theking/.mpv/input.conf'
[   0.055][v][global] config path: 'input.conf' -/-> '/etc/mpv/input.conf'
[   0.055][v][input] Falling back on default (hardcoded) input config
[   0.060][v][osc] Loading script @osc.lua...
[   0.064][v][global] config path: 'scripts' -/-> '/home/theking/.mpv/scripts'
[   0.064][v][global] config path: 'scripts' -/-> '/etc/mpv/scripts'
[   0.064][v][osc] loading mp.defaults
[   0.066][v][osc] loading @osc.lua
[   0.075][v][global] config path: 'lua-settings/osc.conf' -/-> '/home/theking/.mpv/lua-settings/osc.conf'
[   0.075][v][global] config path: 'lua-settings/osc.conf' -/-> '/etc/mpv/lua-settings/osc.conf'
[   0.075][v][osc] lua-settings/osc.conf not found. 
[   0.076][v][cplayer] Run command: define-section, flags=0, args=[showhide, mouse_move script-binding osc/__keybinding1
[   0.076][v][cplayer] mouse_leave script-binding osc/__keybinding2
[   0.076][v][cplayer] , force]
[   0.076][v][cplayer] Run command: enable-section, flags=0, args=[showhide, allow-hide-cursor+allow-vo-dragging]
[   0.076][v][cplayer] Run command: define-section, flags=0, args=[input, mouse_btn0 script-binding osc/__keybinding3
[   0.076][v][cplayer] shift+mouse_btn0 script-binding osc/__keybinding4
[   0.076][v][cplayer] mouse_btn2 script-binding osc/__keybinding5
[   0.076][v][cplayer] mouse_btn0_dbl ignore
[   0.076][v][cplayer] shift+mouse_btn0_dbl ignore
[   0.076][v][cplayer] mouse_btn2_dbl ignore
[   0.077][v][cplayer] , force]
[   0.077][v][cplayer] Run command: enable-section, flags=0, args=[input, ]
[   0.077][v][cplayer] Run command: define-section, flags=0, args=[input_osc, del script-binding osc/__keybinding6
[   0.077][v][cplayer] , default]
[   0.077][v][cplayer] Run command: enable-section, flags=0, args=[input_osc, allow-hide-cursor+allow-vo-dragging]
[   0.077][v][cplayer] Run command: define-section, flags=0, args=[input_forced_osc, , force]
[   0.077][v][cplayer] Run command: enable-section, flags=0, args=[input_forced_osc, allow-hide-cursor+allow-vo-dragging]
[   0.077][v][cplayer] Done loading @osc.lua.
[   0.077][v][ytdl_hook] Loading script @ytdl_hook.lua...
[   0.078][v][global] config path: 'scripts' -/-> '/home/theking/.mpv/scripts'
[   0.078][v][global] config path: 'scripts' -/-> '/etc/mpv/scripts'
[   0.078][v][ytdl_hook] loading mp.defaults
[   0.080][v][ytdl_hook] loading @ytdl_hook.lua
[   0.082][v][cplayer] Run command: disable-section, flags=0, args=[input]
[   0.083][v][global] config path: 'fonts' -/-> '/home/theking/.mpv/fonts'
[   0.083][v][global] config path: 'fonts' -/-> '/etc/mpv/fonts'
[   0.087][v][osd/libass] Shaper: FriBidi 0.19.6 (SIMPLE) HarfBuzz-ng 0.9.27 (COMPLEX)
[   0.087][v][global] config path: 'subfont.ttf' -/-> '/home/theking/.mpv/subfont.ttf'
[   0.088][v][global] config path: 'subfont.ttf' -/-> '/etc/mpv/subfont.ttf'
[   0.088][v][global] config path: 'fonts.conf' -/-> '/home/theking/.mpv/fonts.conf'
[   0.088][v][global] config path: 'fonts.conf' -/-> '/etc/mpv/fonts.conf'
[   0.088][v][osd/libass] Setting up fonts...
[   0.100][v][cplayer] Run command: hook-add, flags=0, args=[on_load, 1, 10]
[   0.100][v][cplayer] Done loading @ytdl_hook.lua.
[   0.100][v][global] config path: 'scripts' -/-> '/home/theking/.mpv/scripts'
[   0.100][v][global] config path: 'scripts' -/-> '/etc/mpv/scripts'
[   0.124][v][global] config path: 'watch_later' -> '/home/theking/.mpv/watch_later'
[   0.124][i][cplayer] Playing: test.mp4
[   0.124][v][cplayer] Running hook: ytdl_hook/on_load
[   0.144][v][osd/libass] Using font provider fontconfig
[   0.144][v][osd/libass] Done.
[   0.146][v][cplayer] Run command: hook-ack, flags=0, args=[on_load]
[   0.150][v][ifo] Opening test.mp4
[   0.151][v][ifo/dvdnav] Opening test.mp4
[   0.153][v][bdmv/bluray] Opening test.mp4
[   0.158][v][file] Opening test.mp4
[   0.158][v][file] Stream opened successfully.
[   0.158][v][demux] Trying demuxers for level=normal.
[   0.906][v][lavf] No format found, try lowering probescore or forcing the format.
[   0.907][v][demux] Trying demuxers for level=unsafe.
[   0.909][v][lavf] Found 'mov,mp4,m4a,3gp,3g2,mj2' at score=1 size=2048.
[   0.910][v][lavf] Found 'mov,mp4,m4a,3gp,3g2,mj2' at score=1 size=4096.
[   0.911][v][lavf] Found 'mov,mp4,m4a,3gp,3g2,mj2' at score=1 size=8192.
[   0.913][v][lavf] Found 'mov,mp4,m4a,3gp,3g2,mj2' at score=1 size=16384.
[   0.917][v][lavf] Found 'mov,mp4,m4a,3gp,3g2,mj2' at score=1 size=32768.
[   0.924][v][lavf] Found 'mov,mp4,m4a,3gp,3g2,mj2' at score=1 size=65536.
[   0.939][v][lavf] Found 'mov,mp4,m4a,3gp,3g2,mj2' at score=1 size=131072.
[   0.969][v][lavf] Found 'mov,mp4,m4a,3gp,3g2,mj2' at score=1 size=262144.
[   1.032][v][lavf] Found 'mov,mp4,m4a,3gp,3g2,mj2' at score=1 size=524288.
[   1.158][v][lavf] Found 'mov,mp4,m4a,3gp,3g2,mj2' at score=1 size=1048576.
[   1.404][v][lavf] Found 'mov,mp4,m4a,3gp,3g2,mj2' at score=1 size=2097152.
[   1.664][v][lavf] Found 'mov,mp4,m4a,3gp,3g2,mj2' at score=1 size=2097152.
[   1.664][v][lavf] No format found, try lowering probescore or forcing the format.
[   1.667][v][cplayer] finished playback, unrecognized file format (reason 4)
[   1.667][e][cplayer] Failed to recognize file format.
[   1.667][i][cplayer] 
[   1.667][i][cplayer] 
[   1.668][i][cplayer] Exiting... (Errors when loading file)
[   1.668][v][ytdl_hook] Exiting...
[   1.672][v][osc] Exiting...



```

Also I just found that .mp3 files "play", there's no sound though. .avi files will play but no sound, same with .mkv. I haven't tried other formats. As before, .mp4 files won't play at all.

---

