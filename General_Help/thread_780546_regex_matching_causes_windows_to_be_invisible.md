---
title: "regex matching causes windows to be invisible"
date: 2008-05-03
forum: General Help
---

### Post by bnl on 2008-05-03
I ran into this strange behavior.  The "Regex Matching" effect causes all windows to be invisible.

I was testing out the effects and was trying "Minimize Effect".  "Animations" had to be disabled.  I decided i didn't like "Minimize Effect" and when i tried to enable "Animations", it said i had to enable "Regex Matching".  Shortly after, all my windows became invisible.  They weren't gone, because i could see them in the desktop switcher on the bottom.

I didn't link "Regex Matching" with the invisible windows at first, because i just assumed that the configuration got borked somehow.  After messing around with my configs and several reboots (and an hour later), i decided to remove all the effects to see what was causing the problem.  To make a long story short, i narrowed it down to the "Regex Matching" effect.  But i wanted my animations!!!  I did notice that it was enabled before when i had animations.  So i looked around to see if i could find a config file.  Sure enough, .config/compiz/compizconfig/Default.ini lists all the plugins.  I first tried adding "animations", but that didn't work.  "animation" (no plural) was the right name for it and i got animations back.

So:

1) Why is "Regex Matching" required for "Animations", if it's possible to enable them without "Regex Matching"?

2) Why does "Regex Matching" make all my windows invisible?  Is something misconfigured somewhere else?

thanks!

(I'm using Xubuntu with xfce4)

---

