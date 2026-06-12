---
title: "Avidemux needs demuxer to open TS video file"
date: 2018-01-04
forum: General Help
---

### Post by lymphor on 2018-01-04
Hello,
I've recently installed Ubuntu 16.04 and realized that Avidemux cannot open TS video files. This is the message I get:
```

Info
Cannot find a demuxer for /media/data/VIDEO.ts

```

This is the mediainfo output of the file:
```

General
ID                                       : 1 (0x1)
Complete name                            : /media/data/VIDEO.ts
Format                                   : MPEG-TS
File size                                : 379 MiB
Duration                                 : 15mn 9s
Overall bit rate mode                    : Variable
Overall bit rate                         : 3 497 Kbps

Video
ID                                       : 256 (0x100)
Menu ID                                  : 1 (0x1)
Format                                   : MPEG Video
Format version                           : Version 2
Format profile                           : Main@Main
Format settings, BVOP                    : Yes
Format settings, Matrix                  : Custom
Format settings, GOP                     : Variable
Format settings, picture structure       : Frame
Codec ID                                 : 2
Duration                                 : 15mn 9s
Bit rate mode                            : Variable
Bit rate                                 : 3 001 Kbps
Maximum bit rate                         : 15.0 Mbps
Width                                    : 720 pixels
Height                                   : 576 pixels
Display aspect ratio                     : 16:9
Frame rate                               : 25.000 fps
Standard                                 : PAL
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Interlaced
Scan order                               : Top Field First
Compression mode                         : Lossy
Bits/(Pixel*Frame)                       : 0.289
Stream size                              : 325 MiB (86%)

Audio #1
ID                                       : 257 (0x101)
Menu ID                                  : 1 (0x1)
Format                                   : MPEG Audio
Format version                           : Version 1
Format profile                           : Layer 2
Codec ID                                 : 3
Duration                                 : 15mn 9s
Bit rate mode                            : Constant
Bit rate                                 : 192 Kbps
Channel(s)                               : 2 channels
Sampling rate                            : 48.0 KHz
Compression mode                         : Lossy
Delay relative to video                  : 10ms
Stream size                              : 20.8 MiB (5%)

Audio #2
ID                                       : 258 (0x102)
Menu ID                                  : 1 (0x1)
Format                                   : MPEG Audio
Format version                           : Version 1
Format profile                           : Layer 2
Codec ID                                 : 3
Duration                                 : 15mn 9s
Bit rate mode                            : Constant
Bit rate                                 : 128 Kbps
Channel(s)                               : 2 channels
Sampling rate                            : 48.0 KHz
Compression mode                         : Lossy
Delay relative to video                  : 10ms
Stream size                              : 13.9 MiB (4%)

Menu
ID                                       : 4096 (0x1000)
Menu ID                                  : 1 (0x1)
Duration                                 : 15mn 9s
List                                     : 256 (0x100) (MPEG Video) / 257 (0x101) (MPEG Audio) / 258 (0x102) (MPEG Audio)
Service name                             : Service01
Service provider                         : FFmpeg
Service type                             : digital television

```

On Ubuntu 16.04 I have all the GStreamer Multimedia Codecs installed, but cannot install ffmpeg, when I try I get this message:
```

Sorry, this did not work
Installation of ffmpeg failed.
Details
Detailed errors from the package manager follow:
snapd returned status code 400: Bad Request

```

I need to mention that with Ubuntu 16.04 I even had problems watching these files, while instead everything was fine with Lubuntu, Windows 7 and Windows 10, including Avidemux was working properly. You can read the full topic here: [https://ubuntuforums.org/showthread.php?t=2381648](https://ubuntuforums.org/showthread.php?t=2381648)

Could you please help me? Thank you! :)

---

### Post by Holger_Gehrke on 2018-01-04
MPEG-TS are mpeg transport streams used for digital video broadcast. They are often damaged between transmission and reception and because of that they are internally split into very small pieces (188 Bytes, AFAIK) with additional data for recovering from transmission errors in every piece (or to quickly resynchronize after switching channels). If these files are recordings from TV they are probably broken in small and insignificant ways in many places, so taking them apart into separate streams and resynchronizing those is necessary. project-x is a demuxer specifically written to split mpeg-ts into elementary streams (one video and one or more audio streams, although I believe there could also be closed captions in a transport stream). You can install it with 'sudo apt-get install project-x', it's in the repositories. Be aware that project-x is written in java, so it'll pull in a java runtime environment (jre) as a dependency. 

And as for ffmpeg: why are you trying to install this as a snap ? Or has the Software-Application made a unilateral decision to try it that way ? ffmpeg is in the repositories, probably not in quite as new a version as the one available as a snap, but at least it installs and works. Install it with 'sudo apt-get install ffmpeg' in a terminal (as if you couldn't guess that by now ...).

Holger

---

### Post by lymphor on 2018-01-28
Hi Holger, sorry for being late with my reply.
Thank you very much for your help, I uninstalled ffmpeg and then reinstalled it via terminal and everything went fine. I don't know why the Software Application displays only the snap version of this software, but your solution managed to fix the issue.
I also tried to remove and reinstall Avidemux, which fixed the TS files issue: I am now able to open and edit them.
Everything is working fine now, thank you so much for your help, it's very appreciated :)

---

