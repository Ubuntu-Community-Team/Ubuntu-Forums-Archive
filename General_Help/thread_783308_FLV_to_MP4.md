---
title: "FLV to MP4"
date: 2008-05-05
forum: General Help
---

### Post by jtreach on 2008-05-05
Heya, I'd like to convert some .flv files to .mp4 (for my ipod) and was wondering how I could achieve this on ubuntu (using software, not vixy.net).

---

### Post by Brucevdk on 2008-05-12
Try using ffmpeg (the example here is converting a video from YouTube):

```

$ sudo apt-get install ffmpeg
$ ffmpeg -i Flash7KTqnM "The Sundays - Summertime.mp4"
[...]
$ file "The Sundays - Summertime.mp4" 
The Sundays - Summertime.mp4: ISO Media, MPEG v4 system, version 1

```

---

