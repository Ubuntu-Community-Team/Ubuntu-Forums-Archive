---
title: "Converting AVI to MPG in Ubuntu"
date: 2006-12-16
forum: General Help
---

### Post by xenoalien on 2006-12-16
Anyone know of a program  that can convert avi videos to mpg?
Thanks

---

### Post by pay on 2006-12-16
Mencoder

---

### Post by insub2 on 2006-12-16
ffmpeg does that.  it runs in the terminal.
heres a link to the doc
[http://ffmpeg.mplayerhq.hu/ffmpeg-doc.html#SEC5]("http://ffmpeg.mplayerhq.hu/ffmpeg-doc.html#SEC5")


***EDIT***
read though that link and found it a little confusing so i did a google search for "ffmpeg avi mpg" and found this page ([http://asuaf.org/~jj/blog/index.php/2006/01/08/convert-google-video-flvs-into-avi-mpg-etcin-linux/]("http://asuaf.org/~jj/blog/index.php/2006/01/08/convert-google-video-flvs-into-avi-mpg-etcin-linux/")) for converting .flv to mpg.

long story short, put this into your terminal and it should be fine:
```
 ffmpeg -i /path_to/file-name.avi -ab 56 -ar 22050 -b 500  -s 320x240 /path_to/file-name.mpg
```

---

### Post by majoridiot on 2006-12-18
avidemux will do it too... with a GUI.

---

### Post by hanzomon4 on 2006-12-18
ffmpeg is the best when it comes to converting videos just be sure to compile your own version if you want make full use of it. I needed to convert videos to ipod format but the one in the repo was not compiled with the needed options. The little switches(options?) look intemidating at first but once you get the hang of it you won't need anything else.

---

