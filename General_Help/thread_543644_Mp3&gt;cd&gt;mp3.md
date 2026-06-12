---
title: "Mp3&gt;cd&gt;mp3 ????"
date: 2007-09-05
forum: General Help
---

### Post by xdanx on 2007-09-05
Quality question! MP3 to CD, Back To MP3?

I have a bunch of mp3s i ripped with a bitrate of 360, and i want them down to 128 for storge reasons, i want more to fit on my mp3 player

the method im using is:

burn mp3s to vital drive
& repripping them in WMP!

the resulting mp3 is now 128!

im not so much bothered about the quailty change between 360 and 128... what i wanna know is does this precess MP3>CD>MP3 degrade the quality even more? more so them ripping direct from the original CD to 128 mp3s!

thanks in advance

---

### Post by marx2k on 2007-09-05
I would think that it would unless you burned them to CD *AS* mp3's meaning you have an mp3 player picking them up from CD... but if you made a CD out of your MP3s to be played in any CD player, I imagine that re-ripping that would lower the quality even further, even if you rip them at 128kbps.  It's going to be compressing already compressed (and expanded, but without quality gain) music

---

### Post by rsambuca on 2007-09-05
Short answer - yes.  When converting from .wav (the lossless format on the original CD) to your 360 bitrate mp3's, you lose quality due to compression issues.  When encoding to the mp3 at a different bitrate, you are encoding from a source that already has less information than the original.  This is similar to the effect you will see with jpeg picture files, which is also a lossy compression format.  If you open, save, open, save, open, save a jpeg file, you lose quality every time even if you make no changes.

---

### Post by ninehrcoma on 2007-09-05
I think the question of whether or not the quality will be degraded is clear. In my opinion 128 is pretty "tinny" sounding. However, if you want to do it anyway, "lame" is the easier options I would think.

```
lame -b 128 song.mp3 song-small.mp3
```

---

### Post by xdanx on 2007-09-05
hey people, thanks for all the advice!

does anyone know of a program that will convert my mp3s to 128? without the extra loss that i would get from going to mp3 to cd then back again? ive tryed a couple but you could hear a lot of extra noise on the tracks!

thanks again in advance!:guitar:

---

