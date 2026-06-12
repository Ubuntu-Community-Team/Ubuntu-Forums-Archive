---
title: "&quot;Signal Out Of Range&quot;. How do i lower my resolution?"
date: 2008-06-03
forum: General Help
---

### Post by AngryBash on 2008-06-03
I kinda selected the wrong resolution, then the [keep settings] box came up (before the resolution was tested) and i clicked it, only to be greeted seconds later with the "Signal out of range" error on my monitor and find that i had selected the wrong resolution. I'm certain i chose 1600x1200 (which my monitor cant/wont handle). I tried editing my xorg.conf (from terminal) and taking out every setting that said my graphics card and monitor can handle 1600x1200 so that it would reset my resolution. But this didn't solve anything. 

Probably a really easy way to fix this that I'm missing. Any ideas guys?

---

### Post by AngryBash on 2008-06-03
Bump. Need help.

---

### Post by bingoUV on 2008-06-03
Run this from terminal 
```

sudo dpkg-reconfigure -phigh xserver-xorg

```

---

### Post by ChameleonDave on 2008-06-03
So, this is on Gnome, is it?  I've just helped someone out with the same problem on Xfce.  It's just a matter of finding the correct config file, and editing it (or just deleting it).

If you log into another desktop environment (Fluxbox, KDE...), that could give you some breathing room.

---

### Post by AngryBash on 2008-06-03
Well. I'm in Ubuntu now. But any attempt to properly set up my xorg.conf leads to the resolution becoming automatically set very high and getting "signal out of range" when i try to start up xserver. So, I'm in 800x600 now, without nvidia drivers. Halp.

Yea. Its gnome.

---

