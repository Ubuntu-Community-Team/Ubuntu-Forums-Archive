---
title: "Beryl Problems"
date: 2006-10-20
forum: General Help
---

### Post by cytutchi on 2006-10-20
Hi there..community!!!
Honestly i tried million and milions of ways i found on the interent but none is complete about how to install Beryl for Kubuntu users (KDE) and Nvdia graphics card!
I tried to make combination of instructions that i found but nothing has worked! I was really lucky to back up my files and still have my Kubuntu working!!
Plz can somebody help me in this situation???
n remember..KDE NVDIA...Beryl

Thenx a lot !
](*,)

---

### Post by jordanmthomas on 2006-10-20
Installation is the exact same in Kubuntu, but you should use
```
kdesu kate
``` instead of ```
gksu gedit
```

Why not try the official instructions at [http://wiki.beryl-project.org](http://wiki.beryl-project.org) ?

---

### Post by PriceChild on 2006-10-20
Beryl is not a beginners subject

*moves to General Help*

BTW my post contains a link to lots of beryl guides, including [http://forum.beryl-project.org/topic-5063-howto-xgl-beryl-kubuntu-dapper-with-nvidia](http://forum.beryl-project.org/topic-5063-howto-xgl-beryl-kubuntu-dapper-with-nvidia)

---

### Post by cytutchi on 2006-10-25
thenx guys for replying to me...the how to you redirected me to really did the work so now it is installed in my system...
actually i used your instructions PriceChild...
so now it is installed in my system but there are still some problems that i am facing if you have any clue for them..???
1. baryl although i login from xgl it is not loaded automatically (actually maybe that is not a problem but it would be ok if when i loged on from xgl the beryl-manager would turn on automaticaly)
2. from firefox and konqueror the minimize or close or maximize buttons have desiperd...actually all the outline of the windows!!!!
3. sometimes when i go to the Kmenu it is opened as full transparend..i cant see nothing ...but if i move with the mouse the side links still open and it is working..its just that i cant see it!
:/
what is happening? :(

thenx a lot again though people!

---

### Post by CarpKing on 2006-10-25
Sounds like you need to add beryl-manager to the startup applications.  This will probably be in something like "Sessions" (I'm not sure how it works in KDE).  The entry in mine is "/usr/bin/beryl-manager."

---

### Post by cytutchi on 2006-10-28
Ok guys...
thenx again..i managed to do it and it is working ok...
but the case that the emerald theme manager doens work properly all the time n some times it crashes and all the theme around the actuall window disapears(meaning the minimize,maximize,close n all that..)
anyway if i restart it works! :/ so maybe somebody could consider it as a bug...
also when i put beryl to autostart it is more usually to crash...if i dont autostart it but...i start it manually then its usually ok!
anyway...Euxaristo! (thenx)

---

