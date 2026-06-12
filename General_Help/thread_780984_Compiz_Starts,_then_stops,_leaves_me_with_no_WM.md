---
title: "Compiz Starts, then stops, leaves me with no WM"
date: 2008-05-03
forum: General Help
---

### Post by cactuswhack on 2008-05-03
I upgraded 7.10 to 8.04.  Dell E1505 with stock 915 chipset.  Compiz works great, except that when I start up.

Compiz loads when I log in.  I can tell it's running by the way my previously opened applications start to open up.  Then the screen goes blank and I lose window management altogether, no title bars, resizing, can't seem to grab focus.

I can start compiz by doing Run Command->'compiz --replace' which works like a champ.  But this is not ideal.  Any ideas?

Thanks!

Tim

---

### Post by z0mbie on 2008-05-03
Compiz is crashing for some reason, I'd install the compiz-fusion icon just to have better GUI control over the windows manager:

```
sudo aptitude install fusion-icon
```

It lets you choose, reload windows manager, so if compiz crashes you can easily reload it or choose Metacity from the notification area.

---

