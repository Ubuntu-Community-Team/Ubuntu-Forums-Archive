---
title: "make screen captures from videos recursive?"
date: 2012-11-01
forum: General Help
---

### Post by sohlinux on 2012-11-01
I have a folder with 50 videos and I need to take some screen shots from each video recursively

the following works for one file only
```

ffmpeg -i name.mp4 -r 1/20 %03d.jpg

```
I tried ```
*.mp4
``` but it said do I want to overwrite the video? I said no then it stopped so what I am doing wrong?

thanks

---

### Post by FakeOutdoorsman on 2012-11-01
You can use a bash "for" loop:
```
for f in *.mp4; do ffmpeg -i "$f" -r 1/20 %03d.jpg; done
```

Unfortunately that will not create unique files names so the next video will overwrite them, or perhaps ffmpeg will halt asking you if you want to overwrite. It's easy to fix. You can give unique output file names:
```
for f in *.mp4; do ffmpeg -i "$f" -r 1/20 "${f%.mp4}-%03d.jpg"; done
```

Alternatively, you can make a separate directory for each video.
```
for f in *.mp4; do mkdir "${f%.mp4}" && ffmpeg -i "$f" -r 1/20 "${f%.mp4}/%03d.jpg"; done
```

If the output files look too crappy then add "-qscale" as an output option with a value between 2-31 (2 is best quality, and 31 is absolute worst).

---

### Post by sohlinux on 2012-11-01
> **FakeOutdoorsman said:**
> You can use a bash "for" loop:
```
for f in *.mp4; do ffmpeg -i "$f" -r 1/20 %03d.jpg; done
```

Unfortunately that will not create unique files names so the next video will overwrite them, or perhaps ffmpeg will halt asking you if you want to overwrite. It's easy to fix. You can give unique output file names:
```
for f in *.mp4; do ffmpeg -i "$f" -r 1/20 "${f%.mp4}-%03d.jpg"; done
```

Alternatively, you can make a separate directory for each video.
```
for f in *.mp4; do mkdir "${f%.mp4}" && ffmpeg -i "$f" -r 1/20 "${f%.mp4}/%03d.jpg"; done
```

If the output files look too crappy then add "-qscale" as an output option with a value between 2-31 (2 is best quality, and 31 is absolute worst).


that's awesome!  a couple more questions if you dont mind, how do I ensure the screenshot is the the same size as the video? some are 640x480 and some are 720x576 and how can I to take 5 screenshots from each video? I think the current setting takes a shot every x seconds because I am getting more shots from some of the longer videos?

thanks :)

---

### Post by FakeOutdoorsman on 2012-11-01
> **sohlinux said:**
> how do I ensure the screenshot is the the same size as the video? some are 640x480 and some are 720x576.

By default the outputs will be the same frame size as the input, so you don't have to do anything extra.

> **sohlinux said:**
> how can I to take 5 screenshots from each video? I think the current setting takes a shot every x seconds because I am getting more shots from some of the longer videos?

Probably a dozen ways to do this, but here's a method using the "select" filter. Let's assume your input frame rate is 24.98 or more accurately 24000/1001 (NTSC film) and it is 120 seconds long in duration:

[list=1]
[*](24000/1001) frame rate * 120 duration = ~2877 total frames
[*]2877 / (number of frames desired - 1) = ~719 frames between output images
[/list]

Please double check my math since I've always been deficient in that area. Which results in:
```
ffmpeg -i input select="eq(n\,0)+eq(n\,719)+eq(n\,1438)+eq(n\,2157)+eq(n\,2876),setpts=N/((24000/1001)*TB)" output-%03d.png
```

You probably don't want the very first frame or the very last so you may want to add a few seconds buffer (±3 seconds in this example, or roughly 75 frames) for the first and last values:
```
ffmpeg -i input select="eq(n\,75)+eq(n\,719)+eq(n\,1438)+eq(n\,2157)+eq(n\,2801),setpts=N/((24000/1001)*TB)" output-%03d.png
```

It's kind of tricky but can be scripted.

---

### Post by sohlinux on 2012-11-02
> **FakeOutdoorsman said:**
> By default the outputs will be the same frame size as the input, so you don't have to do anything extra.



Probably a dozen ways to do this, but here's a method using the "select" filter. Let's assume your input frame rate is 24.98 or more accurately 24000/1001 (NTSC film) and it is 120 seconds long in duration:

[list=1]
[*](24000/1001) frame rate * 120 duration = ~2877 total frames
[*]2877 / (number of frames desired - 1) = ~719 frames between output images
[/list]

Please double check my math since I've always been deficient in that area. Which results in:
```
ffmpeg -i input select="eq(n\,0)+eq(n\,719)+eq(n\,1438)+eq(n\,2157)+eq(n\,2876),setpts=N/((24000/1001)*TB)" output-%03d.png
```

You probably don't want the very first frame or the very last so you may want to add a few seconds buffer (±3 seconds in this example, or roughly 75 frames) for the first and last values:
```
ffmpeg -i input select="eq(n\,75)+eq(n\,719)+eq(n\,1438)+eq(n\,2157)+eq(n\,2801),setpts=N/((24000/1001)*TB)" output-%03d.png
```

It's kind of tricky but can be scripted.

thanks a lot! :)

---

