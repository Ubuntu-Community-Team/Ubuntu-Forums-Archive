---
title: "VLC: Broken playback of V_VP9 in webm/mkv"
date: 2016-09-07
forum: General Help
---

### Post by zuto2 on 2016-09-07
How do I fix broken playback of V_VP9 in webm/mkv for VLC? It works just fin in smplayer (mplayer GUI). That means the file is not corrupt. Here is the output for the "mediainfo" command line program. The [COLOR=#000000][FONT=Ubuntu Mono]Vorbis a[/FONT][/COLOR]udio is working fine. It just has to do with video.

```
Format                                   : MatroskaFormat version                           : Version 4 / Version 2
File size                                : 62.3 MiB
Duration                                 : 17mn 0s
Overall bit rate mode                    : Variable
Overall bit rate                         : 512 Kbps
Writing application                      : Lavf56.40.101
Writing library                          : Lavf56.40.101


Video
ID                                       : 1
Format                                   : V_VP9
Codec ID                                 : V_VP9
Duration                                 : 17mn 0s
Bit rate                                 : 374 Kbps
Width                                    : 1 280 pixels
Height                                   : 720 pixels
Display aspect ratio                     : 16:9
Frame rate                               : 25.000 fps
Bits/(Pixel*Frame)                       : 0.016
Stream size                              : 45.5 MiB (73%)
Language                                 : English
Default                                  : Yes
Forced                                   : No
DURATION                                 : 00:17:00.320000000


Audio
ID                                       : 2
Format                                   : Vorbis
Format settings, Floor                   : 1
Codec ID                                 : A_VORBIS
Duration                                 : 17mn 0s
Bit rate mode                            : Variable
Bit rate                                 : 128 Kbps
Channel(s)                               : 2 channels
Sampling rate                            : 44.1 KHz
Compression mode                         : Lossy
Stream size                              : 15.6 MiB (25%)
Language                                 : English
Default                                  : Yes
Forced                                   : No
DURATION                                 : 00:17:00.382000000
Writing application                      : Google
```

---

