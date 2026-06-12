---
title: "gutsy freezes randomly toshiba satellite"
date: 2008-02-14
forum: General Help
---

### Post by messybricks on 2008-02-14
So... My friend's Toshiba Satellite A135 S2356 (relatively new) is running 7.10, and it occasionally freezes completely.  No keyboard, no mouse.  I realize that this could mean practically anything... I don't know where to start.  Any ideas?

---

### Post by FuturePilot on 2008-02-15
The first thing I would suspect with freezing issues is possibly the graphics driver. What graphics card do you have?
```
lscpi | grep VGA
```

---

### Post by jmadero on 2008-02-17
My girlfriends system has the same issue....have you made any progress with it? It seems with her system that it's when certain programs are opened (not consistent at all). Firefox has triggered a freeze several times, thunderbird once, and a pdf once or twice. It might be something when the system CPU is used heavily. I don't have access to the machine right now but I'm going to run lscpi | grep VGA tomorrow and see what it spits out. It's a bit of a hassle as it freezes at least once a day....switching to another distro would be unfortunate as we are both comfortable with Ubuntu and like how it works (well....when it freezes we stop liking it so much). Any help would be appreciated

---

### Post by messybricks on 2008-02-27
he couldn't figure out how to get the command to work in the terminal that you gave me.  I figured out that it was spelled wrong.  It's "lspci", not "lscpi".  Anyway, here's what's in it:

ATI RC410 [Radeon Xpress 200M]

---

