---
title: "Pulseaudio is hungry for processing."
date: 2008-05-29
forum: General Help
---

### Post by DoritosBR on 2008-05-29
Generally when I'm not doing anything hungry for processing, my cpu usage % just sits low, at 2-3%

But I was playing music on Amarok and noticed the cpu usage % on 20-30 and peaks to up 60%

I looked and it was the **pulseaudio**

I just changed on the xine engine to use alsa, and gone back to normal.

I don't get it, looks like pulseaudio is a downgrade.

Default to only front speakers, processing hungry... (and many other problems reported here on forum)

And to tell the truth, the only real (small) advantage is to use on LTSP, but the advantages are not good enough to get the new problems with it. (Just look at the forums, far more complains than hugs and kisses)

Anyway, is pulseaudio that processing hungry, or there's something you can do to "fix" it (besides **not** using it)

And, on the future will it be better? (less processing hungry?)

---

### Post by gsiliceo on 2008-05-29
Pulseaudio is young, and the ubuntu devs took a chance putting it by default, but its necesary since the features surpase alsa and oss, once the bugs are layed out, we wont the default state in hardy.

---

### Post by Stochastic on 2008-05-30
Well Pulse Audio is an intermediary between xine and alsa in the default setup.  It could be possible that the communication between xine and pulseaudio is not terribly well programed, but I'm just speculating.  You'll find more knowledgeable assistance on the subject in the [Multimedia & Video]("http://ubuntuforums.org/forumdisplay.php?f=334") section of the forums.

Edit: if you do post in multimedia & video, make sure to list what version of xine and pulseaudio you're running.  This info can be found by doing ```
apt-cache policy amarok-xine pulseaudio
```

---

