---
title: "MP4 Playback problems"
date: 2020-04-09
forum: General Help
---

### Post by brenneke on 2020-04-09
Ubuntu 16.04 LTS on older desktop machine, MP4s play with mostly ghost images and intermittent bursts of good images. I have installed restricted-extras and anything else I could find codec related. 

I have tried SMPlayer, VLC and Banshee, all the same problem. 

Plex Media player does play same MP4s perfectly on same machine but am looking for an easier solution to viewing these files with default video player.

Thank you.

---

### Post by TheFu on 2020-04-09
What is "older desktop"?  Around 2013, GPUs started adding HW and driver support for hardware-based video decoding of mpeg2 and h.264 videos.  Before then, they were handled is software so the CPU had to do all the work.   Some media players don't handle HW-decoding, so they use SW-decoding only.

"MP4" doesn't say anything about the video.  .mp4 is just a file container format, not a video format.

in general, adding separate codecs under Linux is a waste of time for non-DRM content.  VLC and mpv compile the v-codec support into those programs.  mpv tries to use HW-decoding whenever possible.

Whenever i see someone having playback issues for video, it usually means their machine isn't running the best GPU drivers.  Check that you are.

---

### Post by brenneke on 2020-04-09
Can you please help me with checking GPU drivers?

Thank you.
[ATTACH=CONFIG]285475[/ATTACH][ATTACH=CONFIG]285476[/ATTACH]

---

### Post by SeijiSensei on 2020-04-09
In my experience, mpv is the best all-around player. However the [build for 16.04]("https://launchpad.net/ubuntu/+source/mpv") is four years old which is an eternity in the world of player software. You could build a copy from source if you want to give that a go: [https://www.howtogeek.com/105413/how-to-compile-and-install-from-source-on-ubuntu/](https://www.howtogeek.com/105413/how-to-compile-and-install-from-source-on-ubuntu/) or you could upgrade to 18.04 or 20.04. I've been running the latter for a while now with nary a hitch.

---

### Post by TheFu on 2020-04-09
I’ve not had issues w/ mpv on 16.04.  Works very well.  Used almost daily, mainly for youtube teaching videos.
```
$ mpv --version
mpv 0.14.0 (C) 2000-2015 mpv/MPlayer/mplayer2 projects
 built on UNKNOWN
ffmpeg library versions:
   libavutil       54.31.100
   libavcodec      56.60.100
   libavformat     56.40.101
   libswscale      3.1.101
   libavfilter     5.40.101
   libswresample   1.2.101
ffmpeg version: 2.8.15-0ubuntu0.16.04.1
```

---

### Post by DuckHook on 2020-04-09
If wanting the latest version, there's always the snap package:```
duckhook@Zeus:~$  snap info mpv
name:      mpv
summary:   a free, open source, and cross-platform media player.
publisher: David Paskevic (casept)
store-url: https://snapcraft.io/mpv
license:   GPL-2.0+
description: |
  mpv is a media player based on MPlayer and mplayer2.
  It supports a wide variety of video file formats,
  audio and video codecs, and subtitle types.
  Remember to connect this snap to the removable-media slot,
  otherwise external media won't be accessible!
snap-id: pWEnXeREW6wdUrc1yMCRXQkuDx3L9f9s
channels:
  latest/stable:    –                          
  latest/candidate: –                          
  latest/beta:      0.26.0 2017-08-03 (1) 98MB -
  latest/edge:      0.27.0 2017-10-09 (2) 99MB -

```

---

### Post by brenneke on 2020-04-09
MPV installed and working perfect - thank you!

---

### Post by TheFu on 2020-04-09
```
 Remember to connect this snap to the removable-media slot,
  otherwise external media won't be accessible!
```

Beware, it, as a snap, cannot play media on NFS storage or local storage outside /home, /media, or /mnt.  Until snap packages address that problem, it cannot be used here.

---

### Post by DuckHook on 2020-04-09
> **TheFu said:**
> Beware, it, as a snap, cannot play media on NFS storage or local storage outside /home, /media, or /mnt.  Until snap packages address that problem, it cannot be used here.
Thanks for the warning. That did slip my mind. Brain cramp.

---

### Post by SeijiSensei on 2020-04-19
You can use SMPlayer as a front-end for mpv and get all its nice GUI controls. In SMPlayer choose Options > Preferences . Then on the General tab, choose mpv from the drop-down box as your "engine," then click OK. Now when you open media files in SMPlayer, they should be played with mpv.

---

