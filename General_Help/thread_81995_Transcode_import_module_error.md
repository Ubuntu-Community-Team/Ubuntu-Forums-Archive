---
title: "Transcode import module error"
date: 2005-10-25
forum: General Help
---

### Post by sandrinux on 2005-10-25
Hy all
I'm trying to use transcode on a Ubuntu 5.10 to translate a file.avi in a DVD reader compliant format, but when i give a:

[B]
transcode -i file01.avi -y ffmpeg --export_prof dvd-pal --export_asr 2 -o file01 -D0 -b224 -N 0x2000 -s2 -m file01.ac3 -J modfps=clonetype=3 --export_fps 25
[/B]

I have this error:

[B]
[transcode] warning : /usr/lib/transcode/import_ffmpeg.so: undefined symbol: dts_init
Loading video import module failed
Did you enable this module when you ran configure?
[transcode] failed to init import modules
[transcode] critical: plug-in initialization failed
[/B]

The problem is that I haven't done the installation from the tarball source code. 
I did it with synaptic, so I haven't ran any "configure" .

Somebody told me in an other forum that may be because I haven't installed the kernel-headers, so i tryed to uninstall transcode, install the linux-kernel-header, then re-install transcode.
But the error message is always the same. :-(

Anibody could help me ?

P.S. Sorry for my bad english :-\

Alessandro Crotti
Biella 
Italy

---

### Post by soulman950 on 2005-10-25
I have the same error but trying to go the other way...
I am tyring to rip a dvd to divx4 and I am getting that same error
so it has to do with a setting of ours, I hope some one out there know the secrets to our successes

---

### Post by KrazyPenguin on 2005-10-25
Getting the same error here !!!

I am trying to go .avi to dvd and it seems my transcode isn't configured yet.

Would removing transcode and installing from source help???

---

### Post by silentbob on 2005-11-06
I'm having the same problem here, has anyone managed to overcome this issue yet?
```
transcode v1.0.1 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
libdvdread: Using libdvdcss version 1.2.8 for DVD access
libdvdread: Can't open file VIDEO_TS.IFO.
[transcode] (probe) suggested AV correction -D 0 (0 ms) | AV 0 ms | 0 ms
[transcode] auto-probing source MVI_0094.AVI (ok)
[transcode] V: import format    | MJPG RIFF data, AVI (V=ffmpeg|A=avi)
[transcode] V: import frame     | 640x480  1.33:1
[transcode] V: bits/pixel       | 0.109 (low)
[transcode] V: decoding fps,frc | 30.000,0
[transcode] V: Y'CbCr           | YV12/I420
[transcode] A: import format    | 0x1     PCM          [11024, 8,1]   88 kbps
[transcode] A: export format    | 0x55    MPEG layer-3 [11024, 8,1]   64 kbps
[transcode] V: encoding fps,frc | 29.970,4
[transcode] A: bytes per frame  | 365 (367.834133)
[transcode] A: adjustment       | 2836@1000
[transcode] A: rescale stream   | 2.000
[transcode] V: IA32/AMD64 accel | sse (sse 3dnowext 3dnow mmxext mmx asm C)
tc_memcpy: using sse for memcpy
[transcode] V: video buffer     | 10 @ 640x480
[transcode] warning : /usr/lib/transcode/import_ffmpeg.so: undefined symbol: dts_init
Loading video import module failed
Did you enable this module when you ran configure?
[transcode] failed to init import modules
[transcode] critical: plug-in initialization failed
```

---

### Post by RAOF on 2005-11-06
[QUOTE=sandrinux]...
[transcode] warning : /usr/lib/transcode/import_ffmpeg.so: undefined symbol: dts_init
...[/QUOTE]
That particular error could probably be solved by installing the "libdts-dev" package in synaptic.

---

### Post by silentbob on 2005-11-07
[QUOTE=RAOF]That particular error could probably be solved by installing the "libdts-dev" package in synaptic.[/QUOTE]
That didn't seem to change anything...
```
transcode v1.0.1 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
libdvdread: Using libdvdcss version 1.2.8 for DVD access
libdvdread: Can't open file VIDEO_TS.IFO.
[tcprobe] RIFF data, AVI video
[transcode] (probe) suggested AV correction -D 0 (0 ms) | AV 0 ms | 0 ms
(probe.c) V magic=0x17, A magic=0x17, V codec=0xa0000010, A codec=0x1
(probe.c) V magic=RIFF data, AVI, A magic=RIFF data, AVI, V codec=MJPG, A codec= PCM
[transcode] auto-probing source MVI_0094.AVI (ok)
[transcode] V: import format    | MJPG RIFF data, AVI (V=ffmpeg|A=avi)
[transcode] V: import frame     | 640x480  1.33:1
[transcode] V: bits/pixel       | 0.109 (low)
[transcode] V: decoding fps,frc | 30.000,0
[transcode] V: Y'CbCr           | YV12/I420
[transcode] A: import format    | 0x1     PCM          [11024, 8,1]   88 kbps
[transcode] A: export format    | 0x55    MPEG layer-3 [11024, 8,1]   64 kbps
[transcode] V: encoding fps,frc | 29.970,4
[transcode] A: bytes per frame  | 365 (367.834133)
[transcode] A: adjustment       | 2836@1000
[transcode] A: rescale stream   | 2.000
[transcode] V: IA32/AMD64 accel | sse (sse 3dnowext 3dnow mmxext mmx asm C)
tc_memcpy: using sse for memcpy
[transcode] encoder delay = decode=40000 encode=40000 usec
[transcode] V: video buffer     | 10 @ 640x480
[transcode] allocating 10 framebuffer (static)
loading audio import module /usr/lib/transcode/import_avi.so
loading video import module /usr/lib/transcode/import_ffmpeg.so
[transcode] warning : /usr/lib/transcode/import_ffmpeg.so: undefined symbol: dts _init
Loading video import module failed
Did you enable this module when you ran configure?
[transcode] failed to init import modules
[transcode] critical: plug-in initialization failed
```

---

### Post by markr on 2005-11-09
I'm also receiving this error, has anyone come up with a solution yet?

Thanks

Mark.

---

### Post by gregorian21 on 2005-11-12
Same problem here. Does anyone have a solution yet?
Thanks!

---

### Post by RAOF on 2005-11-12
You could try using ffmpeg?  I don't use transcode, but I think that ffmpeg will do everything you need.  Either get the ffmpeg package from multiverse, or you can compile it from [http://ffmpeg.sourceforge.net/index.php](http://ffmpeg.sourceforge.net/index.php)

---

### Post by gregorian21 on 2005-11-13
[quote=RAOF]You could try using ffmpeg? I don't use transcode, but I think that ffmpeg will do everything you need. Either get the ffmpeg package from multiverse, or you can compile it from [http://ffmpeg.sourceforge.net/index.php]("http://ffmpeg.sourceforge.net/index.php")[/quote]

Thanks for that. ffmpeg worked like a charm!

---

