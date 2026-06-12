---
title: "How to compress video files"
date: 2020-04-11
forum: General Help
---

### Post by satimis on 2020-04-11
Hi all,

Please advise how to compress .mp4 file without loss of video quality and sound so that I can email the file to friends.

I have tried using ffmpeg according to following link;
ffmpeg-compress-mp4
[https://gist.github.com/lukehedger/277d136f68b028e22bed](https://gist.github.com/lukehedger/277d136f68b028e22bed)

without success, instead the file size increased NOT reduced.

Thanks in advance.

Regards
satimis

---

### Post by GhX6GZMB on 2020-04-11
It's impossible to compress .mp4 files without loss of quality. It's already compressed to the hilt.
The only way to reduce file size is to reduce resolution. You can leave the audio alone, it's only a small fraction of the total file size.

---

### Post by TheFu on 2020-04-11
> **satimis said:**
>  Please advise how to compress .mp4 file without loss of video quality and sound so that I can email the file to friends.

I have tried using ffmpeg according to following link;
ffmpeg-compress-mp4
[https://gist.github.com/lukehedger/277d136f68b028e22bed](https://gist.github.com/lukehedger/277d136f68b028e22bed)

without success, instead the file size increased NOT reduced.

mp4 is just a container, not an encoding. People seem confused by the difference. The video encoding "contained" inside the file can be one of many and each has a mess of different possible settings.  The easiest way to compress video files in the most compatible formats is to use handbrake.

But every compression cycle loses some quality. Otherwise, why wouldn't we just re-re-re-re-re-re-re-re-re-re compress blurays from 25GB to 35MB.  That doesn't work.   Different compression tools have different pros/cons.

i routinely re-compress h.264/aac mp4 video files that were encoded with encoding hardware again into h264/vorb/aac mkv files.  This usually reduces the resulting file size 50-70%.  That's because the hardware encoder is optimized to capture every frame and not care much about the size.

A more versatile container is mkv.  it can hold anything, including whatever an mp4 container holds.  it can also compress audio parts that aren't  normally compressed.

---

### Post by HermanAB on 2020-04-12
If you reduce the size from say 1920 x 1080 to something smaller like 1280 x 720 and reduce the frame rate from say 50 Fps to 25 Fps, the overall size of the video will be 1/4 and nobody will even notice the reduction in quality.  

You could take the frame rate right down to 854 x 480 and 15 Fps and it will still be OK - like an old TV.  

Note that old cartoons run at 7.5 Fps and children are nailed to the screen.  The modern fashion of high frame rates is mostly just that - fashion.  It doesn't make a bad movie look any better.

---

### Post by Yellow Pasque on 2020-04-12
> **ml9104 said:**
> It's impossible to compress .mp4 files without loss of quality. The only way to reduce file size is to reduce resolution.

It's not impossible. It depends on the video codec used. For example, if the mp4 file uses H.264/AVC, you can transcode to H.265/HEVC and get roughly the same quality at 50% of the size.
Of course, transcoding to HEVC or other current gen formats can take a lot of CPU and time.

---

### Post by HermanAB on 2020-04-12
"It's not impossible. It depends on the video codec used." - That is true IIF you have the original lossless video.  If your available video is already compressed, then you need to decompress it and then recompress it, which will make it a little more fuzzy.  The loss in quality is not too apparent if you go down in resolution, but it becomes readily apparent if you keep it the same, or go up in resolution.

---

### Post by SeijiSensei on 2020-04-12
> **HermanAB said:**
> If you reduce the size from say 1920 x 1080 to something smaller like 1280 x 720 and reduce the frame rate from say 50 Fps to 25 Fps, the overall size of the video will be 1/4 and nobody will even notice the reduction in quality.
^The best advice in this thread.

> You could take the frame rate right down to 854 x 480 and 15 Fps and it will still be OK - like an old TV.  
"Old" TVs carried 60 interlaced frames per second, so effectively 30 fps.  I don't know if the full 640x480 frame was broadcast in the early days of the standard though. I think something like 350 lines was more common.

---

