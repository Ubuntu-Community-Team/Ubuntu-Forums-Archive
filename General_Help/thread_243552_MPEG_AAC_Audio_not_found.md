---
title: "MPEG AAC Audio not found??"
date: 2006-08-25
forum: General Help
---

### Post by Xevian on 2006-08-25
I'm using VLC to stream some media in MP4, just built a box around Ubuntu for the first time, and the VLC set-up seems broken... Could just be me, but when I try to encode it just says..

00000303] a52 packetizer: A/52 channels:6 samplerate:48000 bitrate:448000
[00000273] main stream output debug: adding a new input
[00000274] stream_out_transcode private debug: creating audio transcoding from fcc=`a52 ' to fcc=`mp4a'
[00000323] main decoder debug: looking for decoder module: 22 candidates
[00000089] main module debug: using decoder module "a52"
[00000324] main encoder debug: looking for encoder module: 7 candidates
[00000324] ffmpeg encoder debug: libavcodec already initialized
[00000324] ffmpeg encoder error: cannot find encoder MPEG AAC Audio
[00000274] stream_out_transcode private error: cannot find encoder
[00000089] main module debug: unlocking module "a52"
[00000274] stream_out_transcode private error: cannot create audio chain

Any ideas?

---

