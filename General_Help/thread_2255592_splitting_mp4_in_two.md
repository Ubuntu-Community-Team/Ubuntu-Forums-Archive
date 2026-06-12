---
title: "splitting mp4 in two"
date: 2014-12-06
forum: General Help
---

### Post by djpemberton on 2014-12-06
I have tried to split some large .mp4 files in two. I have tried some ffmpeg commands and avidemux. The latter did horribly. The former gives me a great first half, but the video and audio of the second half are always out of sync. Is there a reason for this? And what is the solution?

Thanks

---

### Post by HermanAB on 2014-12-06
You should simply split the file with the 'split' commandline utility.  The video compression algorithm stores a full frame every 15 frames, so it should play no matter how you split it - it would just skip the first few frames.

---

### Post by djpemberton on 2014-12-06
With the "split" command, I *couldn't* split the file at a certain *time* in the video, right? With ffmpeg splitting, the video will still play. It is only that the audio and video is out of sync in the second half.

---

### Post by GrouchyGaijin on 2014-12-06
I usually use kdenlive for video editing.  I'm not running kubuntu, but really have not found anything better for video editing so to me it is worth installing the kde dependencies.

---

### Post by HermanAB on 2014-12-06
If you split the file with 'split' then you will break it at the specified size.  You won't have any control over the timing of the split, unless you do successive tries to get it approximately right.

...and of course, having used 'split', you can easily put the files back together again with 'cat'.

---

### Post by GrouchyGaijin on 2014-12-06
> **HermanAB said:**
> If you split the file with 'split' then you will break it at the specified size.  You won't have any control over the timing of the split, unless you do successive tries to get it approximately right.

...and of course, having used 'split', you can easily put the files back together again with 'cat'.

Personally I have never been able to accurately edit a video file from the command line.  I've tried combining video files using cat but ended up with no sound in the video for some reason.  I am usually a fan of cli applications, but haven't found anything better than kdenlive for video.  Just my two cents, I am far from a video expert.

---

### Post by HermanAB on 2014-12-06
BTW, when I have to edit video, I also turn to kdenlive.  I tried many others and they all suck, but kdenlive sucks a bit less.

---

### Post by FakeOutdoorsman on 2014-12-06
> **djpemberton said:**
> I have tried some ffmpeg commands [...] gives me a great first half, but the video and audio of the second half are always out of sync.
Please show your ffmpeg command and the complete console output. What player(s) did you use to play the output?

---

### Post by GrouchyGaijin on 2014-12-06
Cool the man himself is here.
Listen to FakeOutdoorsman he **IS** a video expert.

---

### Post by FakeOutdoorsman on 2014-12-07
Thanks for the vote of confidence, but now the pressure is on to actually know an answer (tip: wait for someone else to answer first).

---

### Post by djpemberton on 2014-12-08
I have used several variations of codes like this:

ffmpeg -i input.mp4 -vcodec copy -acodec copy -ss 00:00:00 -t 00:30:00 output1.mp4 
ffmpeg -i input.mp4 -vcodec copy -acodec copy -ss 00:30:00 -t 00:30:00 output2.mp4

Everytime I use it for an mp4 file, the first file plays well, but the second is out of sync. However, I just tried it on an avi file. It seems to work great for that.

---

### Post by FakeOutdoorsman on 2014-12-08
Can you show the complete console output from the second command?

---

