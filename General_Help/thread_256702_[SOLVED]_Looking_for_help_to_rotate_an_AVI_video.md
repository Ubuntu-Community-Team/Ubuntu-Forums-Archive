---
title: "[SOLVED] Looking for help to rotate an AVI video"
date: 2006-09-13
forum: General Help
---

### Post by bswilson on 2006-09-13
Friends,

I have been searching through the forums here to find a tool for editing video files, but I have not found the help that I really need (yet).

My digital camera can record AVI formatted videos.  I have been able easily to save these videos to my Ubuntu system, where I can recode them into different formats, etc.  My wife used the camera to record a short video, but she held the camera *vertically*, which means that playback on my computer shows the video as sideways.

I'm trying to find some kind of program that will help me rotate the entire video to be properly horizontal.  Can anyone help me?

---

### Post by beerorkid on 2006-09-13
oh man my wife did the exact same thing.

Took me a bit to get it worked out.  here is the command I used ```
mencoder MVI_4009.AVI -vf rotate=1 -ovc xvid -xvidencopts pass=1:bitrate=687 -oac copy -o gong.AVI
```

using mencoder, the encoder built into mplayer.  The man page is massive

any questions on what the command involves and I can prob help.

problem is that it will squish video if you load it up to youtube or something. like this: [http://www.youtube.com/watch?v=onAWi22ctDY](http://www.youtube.com/watch?v=onAWi22ctDY)

---

### Post by bswilson on 2006-09-13
**beerorkid**, that did the trick for me!  I had skimmed the man pages, and like you said it was horrific.  I didn't realize you could change the aspect ration during the encoder sequence.  VERY helpful.  Thanks a ton; if I figure out how to use *Google Videos* or *YouTube* properly so that the videos won't be squished I'll let you know...

---

