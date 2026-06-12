---
title: "Speed up Wine?"
date: 2007-12-09
forum: General Help
---

### Post by UK-Wobbie on 2007-12-09
Can i speed up Wine in anyway? Some of my games i installed are slow :(
Are there anyway on giving Wine more ram to play with? I know that Wine is not a Emulator.
But i have got like 512 MB of Ram and a 80GB h drive in my computer and the game needs 36 MB of H drive space and 128 MB of Ram.

My computer as got a pentium 4 CPU and the game needs a pentium 3 or bigger.

The Game is called "STOLEN"

I like to know are they are tool what will make Wine faster? Or is there away on making Wine faster it self? :lolflag:

Over Clocking WINE? :mrgreen:


Thanks :)

---

### Post by 3rdalbum on 2007-12-09
Wine takes as much RAM as it needs, so you can't allocate more memory to it; this isn't Mac OS 9 :-P

Go to a terminal and type
```
winecfg
```

Under the Audio (or it might be called Sound) tab, turn off sound. Under Graphics (or Video?) try changing the settings with regard rendering. After each modification, click OK and try the game again.

Other than that, you can only really get a faster computer. Although Wine Is Not An Emulator, it does use a fair bit of processor time to convert Windows calls to Linux ones.

---

