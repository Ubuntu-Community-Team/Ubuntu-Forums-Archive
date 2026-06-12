---
title: "Gutsy screen glitchs when starting applications"
date: 2007-11-07
forum: General Help
---

### Post by imbjr on 2007-11-07
I just started to notice that when I start some applications up (such as Evolution, Pan and Firefox) that there appears on the left side of the screen a region of horizontal glitch (maybe two or more tiny regions of wrongly coloured pixels) that goes maybe 1/8 to 1/4 of the screen to the right. It apears randomly on the vertical. It's very fleeting.

Sometimes, the leftmost pixels of the screen glitch very briefly in a column stretching the full vertical extent of the screen, but only a few horizontal pixels wide. This hasn't happened much though.

I've just changed xorg to only use 60Hz refresh, but that's not stopped the effect.

Note: I have a black background for my desktop which makes the effect more obvious.

Any ideas?

---

### Post by imbjr on 2007-11-07
Well, it's not video memory. The Dell utilities just passed that.

I wonder if its something to do with mtrr. I've re-instated a tweak I had under feisty, but the problem persists and when I do a cat /etc/proc, I'm not convinced the memory map is right. However, if it were something like that I'd have thought the glitching would have been far more extensive.

---

### Post by Noobdaemon on 2008-05-18
ye... at least you guys are lucky enough that it vanishes after a few seconds... i have a permanent white stripe of about 1 inch wide on the left-hand side of my screen... i think it got there after messing with emerald... its a bug in emerald i think because i have never had it before i installed emerald. Anybody please... its annoying as usually all nav is in that edge:S

thanks

Max

---

### Post by imbjr on 2008-05-19
> **Noobdaemon said:**
> ye... at least you guys are lucky enough that it vanishes after a few seconds... i have a permanent white stripe of about 1 inch wide on the left-hand side of my screen... i think it got there after messing with emerald... its a bug in emerald i think because i have never had it before i installed emerald. Anybody please... its annoying as usually all nav is in that edge:S

thanks

Max

Is that a perfectly straight stripe or a glitchy-looking stripe? Just wondering if you have some sort of permanent version of what we see, or something else?

---

