---
title: "Taking Mozilla Firefox Browser Off Ubuntu"
date: 2008-05-12
forum: General Help
---

### Post by OrcaWave on 2008-05-12
Could someone please tell me just how to remove Mozilla Firefox internet browser, and all of it's various features (Thunderbird, etc.) from Ubuntu Hardy Heron OS.

I want to put Opera on instead, which I feel is a far more secure internet browser.

I'm a newbie, so if you could tell how to do this in *steps*, I'd greatly appreciate it.

I know how to remove programs from Windows OS, and how to remove programs from a Mac OS X, but not how to remove them from Ubuntu yet.

Thanks so much for your help!

Orca Wave

---

### Post by tamoneya on 2008-05-12
These should be typed into terminal```
sudo apt-get remove firefox-3.0 thunderbird
sudo apt-get install opera
```

---

### Post by zenwalker on 2008-05-12
2 Ways:

1)Go to Add/Remove app in the menus and remove.
2)Go to menus and choose Synaptic, then search for Firefox or thunderbird. Then right clink on those packages and say remoove. Then apply.
3) via cmd line, using apt-get. Read man pages.

I strongly recommend u to read ubuntu wiki plz.

---

