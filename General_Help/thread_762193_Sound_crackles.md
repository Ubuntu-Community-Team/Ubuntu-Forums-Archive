---
title: "Sound crackles"
date: 2008-04-21
forum: General Help
---

### Post by xaenyx on 2008-04-21
So, I'm trying to get Loki Game's Alpha Centauri planetary pack to work..  I installed it (which went well), patched the game (not quite so well), and make this shell script to start it.  The script does this:

*  Compiz made it like 90% transparent, so it becomes disabled (along with awn and emerald [metacity takes over])

*  It wants to operate in 1024x768, so I used xrandr

*  It only works with oss /dev/dsp, so I enabled /dev/dsp* in pulseaudio and symlinked my headphone dsp1 to dsp.

(smacpack is the app)
```

#!/bin/bash
metacity --replace &
killall avant-window-navigator
xrandr -s 1024x768
gksudo rm /dev/dsp && ln -s /dev/dsp1 /dev/dsp
smacpack
xrandr -s 1280x1024
compiz --replace &
avant-window-navigator &
emerald --replace &

```

Problem is, the sound is all crackly.  Like, it sounds like my speakers are blown out (they work just fine with everything else).  Any ideas?

---

### Post by xaenyx on 2008-04-21
Also, when I actually start playing, it crashes with this output:

```

X Error:  BadMatch
  Request Major code 66 ()
  Error Serial #867
  Current Serial #870

```

I think it might have to do with my composited screen.  Is there any way to disable compositing without logging in/out?  At any rate, it's all very annoying as it worked perfectly out-of-the-box on my openSUSE 10.3 machine.

---

### Post by xaenyx on 2008-04-22
bamp

---

### Post by FluffyElmo on 2008-04-22
Not sure about your problem but you can disable Compiz by right clicking on the desktop, selecting *Change Desktop Background* and then selecting the* Visual Effects* tab.

You can also get to this via *System->Prefernces->Appearance*:)

---

