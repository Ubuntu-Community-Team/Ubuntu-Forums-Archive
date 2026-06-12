---
title: "AVI (english-spanish) to DVD?"
date: 2006-08-01
forum: General Help
---

### Post by iKoo on 2006-08-01
Hi,

I have a problem encoding a .avi file to a .mpg file, cuz the .avi have two audio streams or channels:

Doing ```
ffmpeg -i myfilm.avi
```:

```

Input #0, avi, from 'myfilm.avi':
  Duration: 01:58:53.1, start: 0.000000, bitrate: 1349 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 616x336, 25.00 fps
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 128 kb/s
  Stream #0.2: Audio: mp3, 48000 Hz, stereo, 128 kb/s
Must supply at least one output file

```

The idea is to obtain two output files, the first with the stream 0.0 an 0.1 and the other with 0.0 and 0.2 stream, you know, a .mpeg in english, myfilm_en.avi, and a .mpeg in spanish, myfilm_es.mpeg.

BUT I don't know how I could do this with ffmpeg tool:

```
ffmpeg -i myfilm.avi -target pal-dvd myfilm_en.mpeg myfilm_es.mpeg ...???
``` :confused: :confused: 

Thanks

---

