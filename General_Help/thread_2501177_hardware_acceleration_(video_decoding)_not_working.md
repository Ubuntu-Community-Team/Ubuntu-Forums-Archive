---
title: "hardware acceleration (video decoding) not working, Intel HD Graphic 4600"
date: 2024-09-26
forum: General Help
---

### Post by csh on 2024-09-26
Processor: Intel(R) Core(TM) i5-4590 CPU
Onboard GPU: Intel(R) HD Graphics 4600
RAM: 16GB
OS: Windows 10, Lubuntu 24.04 LTS (dual boot)

Sample video URL (Full HD 1920 x 1080, 60 fps): [http://distribution.bbb3d.renderfarming.net/video/mp4/bbb_sunflower_1080p_60fps_normal.mp4]("http://distribution.bbb3d.renderfarming.net/video/mp4/bbb_sunflower_1080p_60fps_normal.mp4")
Other formats: [http://bbb3d.renderfarming.net/download.html]("http://bbb3d.renderfarming.net/download.html")

Video players (Windows): MPC-HC version 2.3.5, VLC 3.0.21
Web Browser (Windows): Microsoft Edge version 129.0.2792.52

Video players (Lubuntu): VLC 3.0.20 (preinstalled with Lubuntu, not from snap store)
Web browser (Lubuntu): Chromium

My GPU support hardware acceleration for the above video, which use h264 codec.

In Windows 10, when playing the above video by using MPC-HC or VLC, or directly play the video in web browser without download, hardware acceleration works perfectly without any extra configuration, and the video played perfectly.

In Lubuntu, when playing the above video, in web browser and VLC, the video still play, but using software decoder. Hardware acceleration not working at all.

Attached with two files "vlc lubuntu debug (video acceleration automatic) ... .txt" containing VLC debug logs. I split the VLC debug logs into 2 files.

I had run "vainfo" command. Attached here with "vainfo output.txt" file, showing the output of "vainfo" command.

Also attached here with messages shown in chromium's devtools, media section.

How to fix this issue?

---

