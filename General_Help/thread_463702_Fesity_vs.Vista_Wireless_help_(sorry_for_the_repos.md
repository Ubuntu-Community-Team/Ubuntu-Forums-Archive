---
title: "Fesity vs.Vista: Wireless help (sorry for the repost)"
date: 2007-06-03
forum: General Help
---

### Post by skoalman88 on 2007-06-03
I recently bought my gf a Compaq laptop that came with Vista. I'm dualbooting Feisty, but I can't connect to the internet with the WLAN. I have followed the 2 "HOW To's" for broadcom 43xx, but nothing works. I have a broadcom 4311.

Any help is appreciated

---

### Post by bishop9226 on 2007-06-04
i also have broadcom - 

[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

this got me running but you have to make sure to delete any wireless drivers you already have on there.  and for you instead of dl'ing the driver from dell, download your compaq driver for that step.  i think the rest should be the same.

do $user sudo ndiswrapper -l

if it shows you have 0 drivers installed then try those steps, if it has something already there then you need to remove that driver

i forget how to delete it.

---

### Post by Ek0nomik on 2007-06-04
What problems specifically are you having?

Here are two threads that may help:

[http://ubuntuforums.org/showthread.php?t=185174&highlight=4311](http://ubuntuforums.org/showthread.php?t=185174&highlight=4311)

[http://ubuntuforums.org/showthread.php?t=434946&highlight=4311](http://ubuntuforums.org/showthread.php?t=434946&highlight=4311)

---

