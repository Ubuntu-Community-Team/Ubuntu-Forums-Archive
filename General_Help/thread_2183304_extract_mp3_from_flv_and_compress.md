---
title: "extract mp3 from flv and compress"
date: 2013-10-24
forum: General Help
---

### Post by davidtuti2 on 2013-10-24
Hi,

I capture a flv stream from rtsp url:

```
ffmpeg -i file
ffmpeg version 0.8.6-6:0.8.6-1+rpi1, Copyright (c) 2000-2013 the Libav developers
  built on Mar 31 2013 13:58:10 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[flv @ 0xa3a660] max_analyze_duration reached
[flv @ 0xa3a660] Estimating duration from bitrate, this may be inaccurate
Input #0, flv, from 'intereconomia241013_155042':
  Metadata:
    StreamTitle     : 
    StreamUrl       : 
  Duration: 00:03:23.87, start: 0.000000, bitrate: N/A
    Stream #0.0: Audio: aac, 44100 Hz, stereo, s16
At least one output file must be specified

ls file
840K Oct 24 15:53 file

```



Now, I would like extract the audio file and compress it because the recording is about 3hours and I calculate that it could be a size very big

Many thanks and sorry for my english!

---

