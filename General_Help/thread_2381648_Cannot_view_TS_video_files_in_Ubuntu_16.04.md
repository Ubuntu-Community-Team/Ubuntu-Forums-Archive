---
title: "Cannot view TS video files in Ubuntu 16.04"
date: 2018-01-03
forum: General Help
---

### Post by lymphor on 2018-01-03
Hi everybody, for some reason I cannot watch TS video files in Ubuntu 16.04. I have no problems watching them with Lubuntu and Windows 7. How could I fix this?
The messages I get when I try to play them are:

[B]Avidemux 2.6 (QT4)
[/B]```
Info
Cannot find a demuxer for /media/ale/64GB-TV/USB_20171222/VIDEO.ts
```

**Totem Movie Player**
```
An error occurred
Internal data stream error.
```

**VLC**
 ```
[COLOR=#ff0000]Your input can't be opened:[/COLOR]
[COLOR=#000000]VLC is unable to open the MRL 'file:///media/ale/64GB-TV/USB_20171222/VIDEO.ts'. Check the log for details.[/COLOR]
```

According to the "Software" tool I have all the GStreamer Multimedia Codecs installed, but cannot install ffmpeg, when I try I get this message:
```

Sorry, this did not work
Installation of ffmpeg failed.
Details
Detailed errors from the package manager follow:
snapd returned status code 400: Bad Request
```

Could you please help me? Thanks! :)

---

### Post by ajgreeny on 2018-01-03
You are trying to install the snap packaged version of VLC about which I know very little.

Use terminal and commands ```
sudo apt update
sudo apt install vlc
``` which will install the repos version of VLC and probably all the dependencies of VLC which should allow you to play those files.

The files with a .ts suffix are of many different types, and if the above does not solve this problem, it may help us to know more detail of your files, so install **mediainfo** then run command ```
mediainfo path/to/file.ts
``` using the real path to a file, of course with its full filename.

---

### Post by lymphor on 2018-01-03
Thank you very much! I am now able to watch the file using VLC and Totem Movie Player, but I still cannot open it in AviDemux. Here is the mediainfo output:
```
General
ID                                       : 1 (0x1)
Complete name                            : /media/home/partition/VIDEO.ts
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

---

### Post by ajgreeny on 2018-01-03
Can not help with avidemux as I have not used it for years, but I am happy that you got the video to play now.

If you are now happy that this is solved please mark as SOLVED from the Thread Tools menu up-top. It is a great help to users searching the forum.

If you wish to have the avidemux problem solved as well please start a new thread with a new title explaining the problem but add a reference link back to this thread if you wish.

---

### Post by lymphor on 2018-01-04
Thank you very much, your help is highly appreciated, thanks! :)
PS: I have to correct my statement regarding Totem Movie Player, it still doesn't work with this one, but I don't use it.

---

