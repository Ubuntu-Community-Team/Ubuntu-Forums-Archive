---
title: "Batch convert avi files to MP4 with avconv - keep quality"
date: 2014-08-19
forum: General Help
---

### Post by sarahfoxnz on 2014-08-19
for i in *.mp4; do avconv -i "$i" -vcodec copy -ac 2 -strict experimental "out-$i.mp4" ; done

hello.

i found that ffmpeg is now being replaced by avconv & other systems to convert AVI files to MP4

I found the above line that can batch convert multiple AVI files - it seems to work, except the
 picture quality is very bad compared to the original file.


Is there a tutorial / main apge i can go to to find all the options avialable to batch-convert files using avconv ?

(I can find no useful pages re avconv in google,  i expect 'experimental' option is a lower quality function ?)

---

### Post by sudodus on 2014-08-19
You can still use ffmpeg. Many people still think it is good. See these links

[How to Compile FFmpeg and x264 on Ubuntu]("https://trac.ffmpeg.org/wiki/UbuntuCompilationGuide")

[URL="http://ubuntuforums.org/showthread.php?t=786095"]HOWTO: Install and use the latest FFmpeg and x264
[/URL]

---

