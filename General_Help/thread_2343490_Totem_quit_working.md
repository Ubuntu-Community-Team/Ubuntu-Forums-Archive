---
title: "Totem quit working"
date: 2016-11-16
forum: General Help
---

### Post by magpie03 on 2016-11-16
I'm using Ubuntu 14.04 LTS 64 bit. When I choose "Open with video", the player opens but I only have audio and no video. This happened a week or so ago after one of the updates. Videos work fine with VLC. I've searched here and the net but have not found any solutions yet.
Thanks 
Magpie

---

### Post by papibe on 2016-11-16
Hi magpie03.

My first guess would be it's a codec problem.

Could install 'mediainfo':
```
sudo apt-get install mediainfo
```
and then get the codec and file details of the file you want to play:
```
mediainfo video_file
```
Finally. could you copy and paste the output of the last command?

Regards.

---

### Post by magpie03 on 2016-11-16
Thanks papibe. I did "sudo apt-get install mediainfo".
Your next command posted this:
magpie@magpie-MS-7641:~/Documents$ mediainfo video_file VID_20161027_202418244.mp4
General
Complete name                            : VID_20161027_202418244.mp4
Format                                   : MPEG-4
Format profile                           : Base Media / Version 2
Codec ID                                 : mp42
File size                                : 90.3 MiB
Duration                                 : 1mn 14s
Overall bit rate                         : 10.2 Mbps
Encoded date                             : UTC 2016-10-28 00:25:40
Tagged date                              : UTC 2016-10-28 00:25:40

Video
ID                                       : 1
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : High@L3.1
Format settings, CABAC                   : Yes
Format settings, ReFrames                : 1 frame
Format settings, GOP                     : M=1, N=30
Codec ID                                 : avc1
Codec ID/Info                            : Advanced Video Coding
Duration                                 : 1mn 14s
Source duration                          : 1mn 14s
Bit rate                                 : 10.0 Mbps
Width                                    : 1 280 pixels
Height                                   : 720 pixels
Display aspect ratio                     : 16:9
Rotation                                 : 90°
Frame rate mode                          : Variable
Frame rate                               : 30.044 fps
Minimum frame rate                       : 16.006 fps
Maximum frame rate                       : 30.416 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive
Bits/(Pixel*Frame)                       : 0.363
Stream size                              : 88.7 MiB (98%)
Source stream size                       : 88.7 MiB (98%)
Title                                    : VideoHandle
Language                                 : English
Encoded date                             : UTC 2016-10-28 00:25:40
Tagged date                              : UTC 2016-10-28 00:25:40
mdhd_Duration                            : 74095

Audio
ID                                       : 2
Format                                   : AAC
Format/Info                              : Advanced Audio Codec
Format profile                           : LC
Codec ID                                 : 40
Duration                                 : 1mn 14s
Bit rate mode                            : Constant
Bit rate                                 : 128 Kbps
Nominal bit rate                         : 96.0 Kbps
Channel(s)                               : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : 48.0 KHz
Compression mode                         : Lossy
Stream size                              : 1.13 MiB (1%)
Title                                    : SoundHandle
Language                                 : English
Encoded date                             : UTC 2016-10-28 00:25:40
Tagged date                              : UTC 2016-10-28 00:25:40
mdhd_Duration                            : 74112


magpie@magpie-MS-7641:~/Documents$ 

Very sorry about this. Can't remember how to do tags.
magpie

---

