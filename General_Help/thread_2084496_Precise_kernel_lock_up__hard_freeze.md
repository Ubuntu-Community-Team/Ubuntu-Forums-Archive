---
title: "Precise kernel lock up / hard freeze"
date: 2012-11-15
forum: General Help
---

### Post by Budovi on 2012-11-15
**Hi all,**

I'm using **Precise** Pangolin and I like it. It's not my first Ubuntu, I'm working with Ubuntu for couple of years, so I'm not newbie, but not a pro also. Maybe I can told - experienced user level :)

Now... the problem... It is "simple", Ubuntu on my laptop freezes **randomly**. Totally **unpredictable**. To be honest, I experienced same problem in the past and it disappeared before giving me chance to solve it. Now it is irritating me again. I lost my work twice in two days, very frustrated now...

_At the beginning - some very** basic hw** specs..._
Laptop MSI CX-640,, Intel Core i3-3210m,, Nvidia GeForce 520m with Optimus

_Some words about **used software:**_
**Ubuntu 12.04 Precise Pangolin, "fresh" install** (not upgraded)
**Kernel: 3.2.0-32 generic** (default one)
**wacom-dkms** from **ppa:lekensteyn/wacom-tablet** providing updated kernel module for Wacom tablet (I'm using Wacom FUN Pen&Touch)
**ppa:ubuntu-x-swat/x-updates** using for a long time, installed mainly because of old, in the past buggy x-server which caused problems with bumblebee (official repositories were "slow" for me :P )
**bumblebee** package with** bbswitch** kernel module, from **ppa:bumblebee/stable** using it for a long time also (from "beginning" and v3 of bumblebee)
also some **other 3rd party repositories**, but they are just providing **regular software** (mercurial, some lenses, lime theme, oracle java,...)

_**Symptoms:**_
Ubuntu freezes with **no interaction**, under **minimal load**. It is impossible to get any dump, because **any** keys or **input devices** are **working**, including SysRq combinations.
Only hard reset is possible.

Yesterday, I tried to use 2 mainline kernels, 3.3.7 and 3.4.0 with no luck. It installed correctly, but it was unusable: 1, enormous battery drain 2, longer boot with "intel MUX INFO call failed" messages 3, unable to change power state any way (sleep, shutdown, nothing) 4, minimum hardware were working (also stupid HID USB mouse didn't work)

So I'm back at 3.2.0-32... I would appreciate any help, if you need any further information or tests/debugging, I have no problems with providing almost anything :D

Searching solutions for this kind of problem is hard, people are just mixing lot of unrelated problems and then there is no reasonable solution.

Thanks a lot for your time in advance,
Budovi

---

