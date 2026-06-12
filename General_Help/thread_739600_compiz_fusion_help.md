---
title: "compiz fusion help"
date: 2008-03-29
forum: General Help
---

### Post by keeanrunt on 2008-03-29
ok so heere is what ive done, tried the G.I.T method  didn't work, i looked for compiz on package manager, and could not find any thing on add/removie for adcanced desktop effects.  so what do i do  major help needed.  just looking for the easiest safest wat to get compiz.  i have a intel graphics card and don't know if i need any additional drivers or. and does anyone think beryl is better and is it easier to install?  thanx to anyone who can help:confused:

---

### Post by Triggerhapp on 2008-03-29
Hey, what version of Ubuntu do you have installed? This was my first mistake when I looked into this, I was using Dapper

---

### Post by jken146 on 2008-03-29
Install the package **compizconfig-settings-manager** -- you can search for it in Synaptic or open a terminal and type ```
sudo aptitude install compizconfig-settings-manager
```
Then run it from System -> Preferences -> Advanced Desktop Effects or by typing ```
ccsm
```

---

### Post by castoroil97 on 2008-03-29
in installed that and when I typed 'ccsm' I got :

Traceback (most recent call last):
  File "/usr/bin/ccsm", line 24, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
  File "/usr/lib/python2.5/site-packages/cairo/__init__.py", line 1, in <module>
    from _cairo import *
ImportError: /usr/lib/python2.5/site-packages/cairo/_cairo.so: undefined symbol: cairo_clip_extents

---

### Post by castoroil97 on 2008-03-29
I just upgraded to Gutsy and I used to have Feisty with Beryl

---

### Post by castoroil97 on 2008-03-29
This thread helped
[http://ubuntuforums.org/showthread.php?p=4614249#post4614249](http://ubuntuforums.org/showthread.php?p=4614249#post4614249)

and the fix is here
[https://bugs.launchpad.net/libcairo/+bug/129816/comments/11](https://bugs.launchpad.net/libcairo/+bug/129816/comments/11)

---

### Post by keeanrunt on 2008-03-30
at the moment im using fiesty fawn, if thats how u spell it, i got it using wubi idk if that matters or it i'ts missing anything but if it is fell free to fill meh in.  thanx

---

