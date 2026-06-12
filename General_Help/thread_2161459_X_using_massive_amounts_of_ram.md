---
title: "X using massive amounts of ram"
date: 2013-07-10
forum: General Help
---

### Post by JaySeeJC on 2013-07-10
My system seems to be randomly slowing to a crawl, and looking at htop's output Lightdm is using massive amounts of ram, 40%+ with 24gb ram. Anyone have any idea why or any workarounds or fixes to this problem?

EDIT:
It seems to be X that's eating all my ram. I noticed there being "lightdm" in the command and assumed. Anyways, the command line that's eating all the ram is as follows:
```
/usr/bin/X :0 -core -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none
```

---

### Post by silv3rm00n on 2013-07-11
You mean, X is eating GBs of RAM ?
On my system Xorg consumes around 24MB of ram which appears ok.

---

### Post by claracc on 2013-07-11
What is the ubuntu release in your system?, what are your hardware specs?

Perhaps, are you using an intensive graphics resources application as gimp or any other?

Also, what is your graphics card?, do you need any proprietary driver for it?

---

### Post by rnerwein on 2013-07-11
> **JaySeeJC said:**
> My system seems to be randomly slowing to a crawl, and looking at htop's output Lightdm is using massive amounts of ram, 40%+ with 24gb ram. Anyone have any idea why or any workarounds or fixes to this problem?

EDIT:
It seems to be X that's eating all my ram. I noticed there being "lightdm" in the command and assumed. Anyways, the command line that's eating all the ram is as follows:
```
/usr/bin/X :0 -core -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none
```
hi
would be nice to see the output of "top" with the following lines:
Cpu(s):  0.3%us,  2.4%sy,  0.0%ni, 96.8%id,  0.4%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3790556k total,  2013360k used,  1777196k free,   234836k buffers
Swap:  6570508k total,        0k used,  6570508k free,   816340k cached

ciao

---

