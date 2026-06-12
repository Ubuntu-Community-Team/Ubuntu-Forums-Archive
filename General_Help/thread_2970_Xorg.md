---
title: "Xorg?"
date: 2004-11-02
forum: General Help
---

### Post by keffo on 2004-11-02
Hey

Im about to install Ubuntu when I come home.. But im worried about
one thingie. Last time when I ran Slackware 10 it came wiff teh Xorg
instead of X11 or summit.. AND it totally screwed up, when playing
for example Tuxracer sometimes when I changed menu it jumped out
to fullscreenterminal and X where killed.. No-one could help me, but
I found a thread somewhere that ATI + Xorg == buggin'

Does anyone in here knows anything about this?
And, easy way to install GFX drivers for ATi Radeon cards, I mean..
Last time it was quite friggin' hard (thx to Fackamato tho')

---

### Post by diebels on 2004-11-02
The X11 for ubuntu warty is 4.3.99 + lots of patches made by ubuntu developers and patches backported from xorg. Works very well. Try it and ask for help if it doesn't work.

---

### Post by keffo on 2004-11-03
ok, but if you have a ATI card, how do you install your drivers? Just wanna know your way todo it.. Since there must be a easy way :> [-X

---

### Post by ulrich on 2004-11-03
you install your ati-drivers as described here:

[http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto)

no voodoo or black magic required :)

---

### Post by daniels on 2004-11-03
While we're on the topic ...

```
daniels@catsby:~/x/xlibs/merge/X11% xdpyinfo | grep -i vendor
vendor string:    The X.Org Foundation
vendor release number:    60801000
```

We'll release packages as soon as they're ready for widespread testing -- there are still a few bad bugs but overall it's looking great!

---

