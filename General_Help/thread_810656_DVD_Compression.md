---
title: "DVD Compression"
date: 2008-05-28
forum: General Help
---

### Post by scouser73 on 2008-05-28
I have quite a few films on my external HDD all of which are in AVI format. I was trying to do an .ISO the other day but Brasero stated that the film was 112%, this being on a 4.7Gb blank DVD.

Is there any program that can compress these down so it will fit onto a 4.7Gb disc?


Disclaimer - All the films on my hard drive I have backed up from original discs.

---

### Post by bingoUV on 2008-05-28
Install mplayer and mencoder from repositories. From command line, 
```

mplayer /path/to/video/file

```
and press q immediately to quit player. Read the output of mplayer. There will be lines starting with VIDEO, and AUDIO. These will give you the bitrate. Video bitrate in kbps, e.g.
```

VIDEO:  [FMP4]  352x240  24bpp  29.970 fps  **_499.9 kbps_** (61.0 kbyte/s)

```

and audio bitrate in kbit e.g.
```

AUDIO: 48000 Hz, 2 ch, s16le, **_112.0 kbit_**/7.29% (ratio: 14000->192000)

```


Since you are exceeding your target size by 12%, decide appropriate bitrates for your audio and video. e.g. decrease both around 15%. Note that abitrate needs to be in multiples of 16. Now, encode using mencoder
```

mencoder /path/to/video/file -oac lavc -ovc lavc -lavcopts abitrate=<insertNewAudioBitrateHere>:vbitrate=<insertNewVideoBitrateHere>

```

---

