---
title: "Fuppes"
date: 2007-10-12
forum: General Help
---

### Post by hebetude on 2007-10-12
Fuppes, apparently the only media server for PS3/XBOX, is giving me some problems while trying to compile it.  I got past the first few missing dev libraries, but now I'm having transcoding problems during ./configure.  Here's the spitout from configure status

```

  SUMMARY

  audio transcoding disabled

  video transcoding (experimental)
  ffmpeg     : disabled


  iconv      : enabled
  uuid       : disabled
  taglib     : disabled
  ImageMagick: disabled
  libavformat: disabled

GNOME
  panel applet : disabled
  libnotify    : disabled

```

Why is ffmpeg support disabled, I did a search for ffmpeg related libraries and did not see any?

Thanks,

---

### Post by hebetude on 2007-10-12
I even tried installing transcode since it uses ffmpeg to do transcoding, still it says ffmpeg is disabled

---

### Post by hebetude on 2007-10-12
answer: ./configure --enable-video-transcoding

---

