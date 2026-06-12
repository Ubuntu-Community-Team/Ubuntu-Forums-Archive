---
title: "Problem with sound under 7.04 (no problem with 6.10)"
date: 2007-07-27
forum: General Help
---

### Post by anewbie on 2007-07-27
I upgraded ubuntu and sound from mpeg players (such as vlc/mplayer) stopped working. H owever, it still works fine from tvtime. Not sure how tvtime differs. Also, I'm not sure if it happened on the distupgrade or one of the software patches shortly after that. Given that it works with tvtime I would think it might be a solvable issue but not sure where to look (the lines from mplayer seem to indicate all is ok). Maybe it is a gnome issue ?

Any suggestions ?

(vaguely i think this problem might have started after I hit the mute button in mplayer but not sure because also been doing updates as needed...)
(also I tried rebooting to resolve the problem - still mute on mplayer/vlc but works fine with tvtime)

I found the problem. init.d/alsa-utils reset broke the sound for the tv but restore the sound for mplayer but I knew which setting to enable to renable sound for the tv (mic in) - so now I understand why there was no sound but not how it got into that state nor why the state persist after reboot. hum. from some of the web searches i did this seems related to the kernel upgrade after the original fiesty install which is around the time that soudn stopped working for me so might be something in that... btw the kernel is 2.6.20-16

---

