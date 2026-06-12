---
title: "QTWebEngineProcess (Chromium) plays randomly audio I watched some time ago"
date: 2020-12-11
forum: General Help
---

### Post by max45345 on 2020-12-11
Hi,

randomly the process "QTWebEngineProcess" plays the audio of a video I watched a couple of months ago. I can see in the audio mixer that the sound comes from Chromium and when I kill the process QTWebEngineProcess the audio stops for a few minutes.

I have already removed Chromium with apt  but nothing changed.

What can I do? I'm on Kubuntu 18.04 LTS.

---

### Post by max45345 on 2021-01-07
What information should I provide to get an answer?

> [FONT=monospace][COLOR=#000000]$ ps -ef[/COLOR][/FONT]
max     7668  7662  0 09:48 ?        00:00:00 /usr/lib/x86_64-linux-gnu/qt5/libexec/QtWebEngineProcess --type=zygote --lang=en-US
max     7670  7668  0 09:48 ?        00:00:00 /usr/lib/x86_64-linux-gnu/qt5/libexec/QtWebEngineProcess --type=zygote --lang=en-US
max     7687  7670  0 09:48 ?        00:00:00 /usr/lib/x86_64-linux-gnu/qt5/libexec/QtWebEngineProcess --type=renderer --disable-accelerated-video-decode --disable-gpu-memory-buffer-video-frames --disable-shared-workers --enable-threaded-compositing --disable-webrtc-hw

---

