---
title: "Video thumbnails working except .ASF after"
date: 2018-07-28
forum: General Help
---

### Post by davidboom on 2018-07-28
I am using Ubuntu 18.04 Minimal Installation, I noticed none of my video thumbnails displayed.

So I followed the instructions here: 

[https://askubuntu.com/questions/1034595/thumbnails-not-showing-in-video-in-ubuntu-18-04](https://askubuntu.com/questions/1034595/thumbnails-not-showing-in-video-in-ubuntu-18-04)

I used:

```
sudo apt install ffmpegthumbnailer
```

This fixed thumbnails for a number of formats but not .ASF.

I also installed ffmpg.

The link above references gstreamer0.10-ffmpeg but no longer exists.

/usr/share/thumbnailers/ffmpegthumbnailer.thumbnailer contains this which includes ASF:

```
[Thumbnailer Entry]
TryExec=ffmpegthumbnailer
Exec=ffmpegthumbnailer -i %i -o %o -s %s -f
MimeType=video/jpeg;video/mp4;video/mpeg;video/quicktime;video/x-ms-asf;video/x-ms-wm;video/x-ms-wmv;video/x-msvideo;video/x-flv;video/x-matroska;video/webm;video/mp2t;
```

---

