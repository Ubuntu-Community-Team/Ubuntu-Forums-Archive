---
title: "Simple Screen Recorder Optimization"
date: 2016-12-14
forum: General Help
---

### Post by irongolem0982 on 2016-12-14
Just got a new CPU that allows me to play my game and record at 60 fps with SSR's default settings, what my question is is what are my optimal settings, as i want to conserve CPU time as much as possible (for other reasons)

Which container should I use for minimum CPU time? default is matroska. avaliable: matroska, mp4, webM, Ogg and Other.'

Which codec should I use for minimum CPU time? default is H.264. H.264, Vp8 and Theora.

if H.264 what should the Constant Rate Factor be set at? and what preset should I use? 


Thanks In advance!


Update: originally my initial tests were carried out with an extremely old graphics card, don't laugh at me, the Nvidia Geforce 7600 GT.... which is what i have had in that pc for forever. But i had another (dont laugh) GT 610 lying around so i stuck that in there and got great results! (kind of, see below)




for context:


Here is how the 7600 performed:
60 fps game and 60 fps recording (via OpenGL) with 10% cpu to spare and 90%GPU Usage - no screen tearing
AND
60 fps game 60 fps recording (via fixed window) with 15% cpu to spare and 70% GPU - SCREEN TEARING


Here is how the GT 610 performed:
30-40 fps game and 30-40 fps recording (via OpenGL) constantly going up and down in that fps range with 30% cpu to spare and 80% GPU usage - no screen tearing
AND
60 fps game and 60 fps recording (via fixed window) with 30% cpu to spare and 60-70% GPU usage - SCREEN TEARING


I recorded for an hour and a half (on 610 @30fps, non OpenGL) then went back and watched it, the screen tearing really gets to you. I tried 60 fps non OpenGL and it was better because of the higher framerate and all but still gets me. 


Why would the 7600 get better OpenGL recording than the 610?? they are both pretty crappy but in terms of specs the 610 beats it in everything but memory bandwitdth (128 vs 64 bit) (also 256mb vs 2048mb) is there a driver setting i can change to help with this? or should i just go back to my ancient card?


i really like the 610 alot better in terms of normal desktop performance and video decoding but if i must go back to the 7600 gt then i will 


@TheFU you mentioned getting an external recorder, i would love that option but im a starving college student so every cent counts at the moment (which is also why i have antiquated technology)


Another thing: the 7600 is using OpenGL 2.1 whereas the 610 reports 4.5.0 maybe run the game in 2.1 somehow?


Summary of my questions:
60fps w/Screen tearing? OR 30 fps W/o?
7600? or 610?
Driver option to speed-up OpenGl recording?

---

### Post by TheFu on 2016-12-14
If you really care about minimizing CPU, get an external video recording device. They are pretty cheap if you only need 1080p or less resolution. Just $65-$75.

I don't think the container matters. MKV is the most versatile.  Using h.264 is pretty much required for compatibility of hidef recordings.  The only thing left to control is the transcoding speed (which leads to huge file sizes).  We can always re-transcode/encode later to save 80%+ of the space.  There's always a trade-off between file size and encoding CPU required.  For h.264, the lower the CRF, the more CPU and fewer artifacts.  Trade-offs.  I wouldn't bother with a CRF below 19 - that doesn't show any artifacts that I can see.  At 22, I see lots of artifacts, but CPU is much less.

Trade-offs.

Really - just off load this to an external device.

---

### Post by irongolem0982 on 2016-12-14
Update: originally my initial tests were carried out with an extremely old graphics card, don't laugh at me, the Nvidia Geforce 7600 GT.... which is what i have had in that pc for forever. But i had another (dont laugh) GT 610 lying around so i stuck that in there and got great results! (kind of, see below)


for context:

Here is how the 7600 performed:
60 fps game and 60 fps recording (via OpenGL) with 10% cpu to spare and 90%GPU Usage - no screen tearing
AND
60 fps game 60 fps recording (via fixed window) with 15% cpu to spare and 70% GPU - SCREEN TEARING

Here is how the GT 610 performed:
30-40 fps game and 30-40 fps recording (via OpenGL) constantly going up and down in that fps range with 30% cpu to spare and 80% GPU usage - no screen tearing
AND
60 fps game and 60 fps recording (via fixed window) with 30% cpu to spare and 60-70% GPU usage - SCREEN TEARING

I recorded for an hour and a half (on 610 @30fps, non OpenGL) then went back and watched it, the screen tearing really gets to you. I tried 60 fps non OpenGL and it was better because of the higher framerate and all but still gets me. 

Why would the 7600 get better OpenGL recording than the 610?? they are both pretty crappy but in terms of specs the 610 beats it in everything but memory bandwitdth (128 vs 64 bit) (also 256mb vs 2048mb) is there a driver setting i can change to help with this? or should i just go back to my ancient card?

i really like the 610 alot better in terms of normal desktop performance and video decoding but if i must go back to the 7600 gt then i will :P

@TheFU you mentioned getting an external recorder, i would love that option but im a starving college student so every cent counts at the moment (which is also why i have antiquated technology)

Another thing: the 7600 is using OpenGL 2.1 whereas the 610 reports 4.5.0  maybe run the game in 2.1 somehow?

Summary of my questions:
60fps w/Screen tearing? OR 30 fps W/o?
7600? or 610?
Driver option to speed-up OpenGl recording?


Thanks!

---

