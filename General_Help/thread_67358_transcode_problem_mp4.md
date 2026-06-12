---
title: "transcode problem mp4"
date: 2005-09-20
forum: General Help
---

### Post by sfabel on 2005-09-20
Hi everybody,

I'm not even sure this is the right forum, if you know a better place to ask, just tell me so.

I have a couple of MPEG4 (*.mp4) video clips here, which are decoded by VLC without a problem, but not with Windows Media Player. Since the person I am trying to send this to is only using WMPlayer, and not very computer literate, I planned on transcoding the file to something less problematic.

I am an absolute beginner when it comes to transcode, and I am not even sure if that's the right tool to use. The output of my transcode session is as follows:

```

transcode v0.6.14 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
[transcode] (probe) suggested AV correction -D 0 (0 ms) | AV 0 ms | 0 ms
[transcode] auto-probing source test.mp4 (ok)
[transcode] V: import format    | unknown QuickTime (V=mov|A=mov)
[transcode] V: import frame     | 320x240  1.33:1
[transcode] V: bits/pixel       | 0.938
[transcode] V: decoding fps,frc | 25.000,3
[transcode] V: Y'CbCr           | YV12/I420
[transcode] A: import format    | 0x2000  AC3          [   0,16,0]
[transcode] A: export           | disabled
[transcode] V: encoding fps,frc | 25.000,3
[transcode] A: bytes per frame  | 0 (0.000000)
[transcode] A: adjustment       | 0@1000
[transcode] V: IA32 accel mode  | sse2 (sse2 sse mmxext mmx asm C)
tc_memcpy: using mmxext for memcpy
[transcode] warning : no option -o found, encoded frames send to "/dev/null"
[transcode] V: video buffer     | 10 @ 320x240
[import_mov.so] v0.1.2 (2002-05-16) (video) * | (audio) *
[export_null.so] v0.1.2 (2001-08-17) (video) null | (audio) null
[import_mov.so] codec=mp4a, rate=0 Hz, bits=0, channels=0, samples=11546
**error: unsupported sample bits: 0**
audio import module error: OPEN failed
[transcode] critical: failed to open input source

```

That's transcode run just with the "-i" option. I've highlighted the problem (sample bits line). How can I set the sample bits or autoprobe for them, or is there even a way to correct the problem with transcode?

Thanks for your help.

Stephan

---

