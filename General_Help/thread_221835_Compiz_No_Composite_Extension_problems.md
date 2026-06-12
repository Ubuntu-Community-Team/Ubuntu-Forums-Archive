---
title: "Compiz: No Composite Extension problems"
date: 2006-07-24
forum: General Help
---

### Post by dmo580 on 2006-07-24
I have an ATI card so please don't tell me to add those few lines about extensions into my xorg.conf. If I do, my screen screws up.

Here's what happens.

```
dmo@dmo-laptop:~$ sudo startcompiz
compiz.real: Connection Error (No reply within specified time)
compiz.real: Couldn't initiate D-BUS connection
compiz.real: Disabling D-BUS Service
compiz.real: No composite extension
dmo@dmo-laptop:~$ fglrxinfo

dmo@dmo-laptop:~$ fglrxinfo -display :1
display: :1.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY/RADEON 9000 DDR Generic
OpenGL version string: 1.3.1080 (X4.3.0-8.26.6)

```

Running Dell 600m w/ Mobility Radeon 9000.

3D is clearing working as glx_gears gives me nice fps.

Please do NOT point me to guides, because I have followed the compiz and fglrx guides word by word. I have searched the Wiki, and I would appreciate it if someone knows how to deal with this specifically. I see that most people respond showing what they did to get Compiz working, which is simply the guide I followed. That's not helping me, and so I need a specific fix for this. Plus I can see this is a prob lem for many ppl. Thanks.

---

### Post by philippe_carlo on 2006-07-24
Same probs here. Apparently, ATI screwed up the driver for mobility cards in such a way that compiz does not work any more. Bummer.

---

### Post by dmo580 on 2006-07-24
Yea, boo. I got it to work with Mesa last week when I tried out Compiz for the first time, but then when I tried to install ATI drivers, everything crashed and I reinstalled Dapper. Now I can't get Compiz to work with Mesa either (same composite extension error) and nor does it work with fglrx =(

---

### Post by dmo580 on 2006-07-30
bump bump?

---

