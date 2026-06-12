---
title: "ffmpeg won't scale video"
date: 2005-10-17
forum: General Help
---

### Post by glug101 on 2005-10-17
Yep, that's correct.  No matter what command lines I pass to ffmpeg, I get the same output frame size and frame rate as the input video.  Frustrating, because I'm used to using the simple command
```
ffmpeg -hq -target ntsc-svcd -i <input file> <output file>.mpg
```
in order to create files for svcd's.  

I tried using the in depth commands (list available by typing ffmpeg without options) but even by specifying 480x480 resolution with a 29.97 fps output, I still get ~24 fps and the same output resolution as the input video.

Ouput frame rate and resolution verified by Mplayer, because it is NOT svcd standard and will not work correctly in my dvd player this way.  I have also tried uninstalling ffmpeg and going as far as compiling it from source to try and clear this out.  No luck.

Anybody else see this before or have any suggestions?  I would be much obliged.

---

