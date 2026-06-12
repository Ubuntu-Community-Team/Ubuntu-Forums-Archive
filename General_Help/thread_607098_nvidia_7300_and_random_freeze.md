---
title: "nvidia 7300 and random freeze"
date: 2007-11-08
forum: General Help
---

### Post by ultimatsz on 2007-11-08
from many of the post i see... many of the random lockup or freeze is due to nvidia 7300, apparently my driver is also 7300, i have random freeze with mouse and compiz still working (meaning windows will go black and white). what is the problem of this? memtested and no probs.

---

### Post by FuturePilot on 2007-11-08
I've heard this happens with the GeForce 7xxx cards and dual core CPUs because of a regression that showed up in the 100.14.11 driver. What kind of CPU do you have and what driver are you using? You can find the driver version with this
```
cat /proc/driver/nvidia/version
```

---

### Post by ultimatsz on 2007-11-08
i know 100.14.11 have the problems.. mine is 100.14.19

my computer is intel core 2 duo t5600
1.83ghz 667mhz fsb 2mb l2chache

nvidia geforce go 7300 128mb

---

### Post by FuturePilot on 2007-11-08
That sounds like the problem. The regression is still present in the 100.14.19. I've heard a few people say the 100.14.23 has fixed it. You can use [Envy]("http://albertomilone.com/nvidia_scripts1.html") to install the 100.14.23 driver. But I do know for sure the other driver that works is 100.14.09. You would have to manually install that one though.

---

### Post by ultimatsz on 2007-11-09
somehow i cannot install envy.

it got stuck at prepareing to configure dh-make

i m using gutsy.

i m not sure about manual installation. because i have to set to different levels.which i may screw up ..

---

### Post by bulldog on 2007-11-09
Do you use the.deb for Gutsy?
[http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.8-0ubuntu12_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.8-0ubuntu12_all.deb)

---

### Post by ultimatsz on 2007-11-09
i finally can install envy.. after some problems over and again.. i installed 100.14.23 driver on my laptop.
somehow.. the sudden lockup is still there.. but not as often. as usual. the windows become black and white. but compiz still works.

not as often already... thanks for the help guys...

i think the problem lies with the core2duo processor.. i will go look out for that

hmm.. if it is that the driver 100.14.23 still have the bug... maybe i wil have to wait till they update it then.....

---

