---
title: "Black Bars Around Edge of Monitor"
date: 2012-11-19
forum: General Help
---

### Post by electrojustin on 2012-11-19
Hello all,
I have an Acer H233H monitor connected to my Radeon HD 6670 graphics card and had black bars around the edges at 1920x1080. I fixed this by increasing the overscan, but the problem reappears every boot-up and I have to lower the overscan then raise it again to fix it. Any suggestions as to how I might make this problem go away completely? So far I've tried increasing the refresh rate to the appropriate 75 Hz, but Catalyst won't let me, and overriding with xorg.conf does nothing.

---

### Post by electrojustin on 2012-11-23
bump?

---

### Post by efflandt on 2012-11-23
You probably have to run Catalyst as root (using gksu) to make permanent changes.  I don't have ATI video on this computer, so not sure of Catalyst program name (maybe amdcccle?).

---

### Post by QIII on 2012-11-24
```
gksudo amdcccle
```

it is possible you may need to use the fully qualified path if you have installed using a method other than the repo, maybe something like

```
gksudo /usr/lib/fglrx/bin/amdcccle
```

---

### Post by electrojustin on 2012-11-24
I do run Catalyst as root with "gksudo amdcccle"; I had to use that to configure my second monitor and make the fix in the first place. The fix stays according to the little overscan slider, but I have to turn it down then up again to fix it again every reboot. Would running the full path make a difference if it already works from just typing "gksudo amdcccle"? Also, a quick update: Everything seems to be OK for this reboot-which is odd since that hasn't really worked in a few months. I think it may have something to do with me interrupting the booting process with a hard restart midway through. I rebooted again to see if it would stay, and it did, but I'm not sure how long it will last.

---

### Post by electrojustin on 2012-11-29
OK after a couple days, it looks like the fix is stable :D. Despite the fact that hard rebooting in general is a bad idea-let alone during reboot-it seems to have done the trick.

---

