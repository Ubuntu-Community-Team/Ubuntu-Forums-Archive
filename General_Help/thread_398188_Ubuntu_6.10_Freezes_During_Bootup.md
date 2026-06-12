---
title: "Ubuntu 6.10 Freezes During Bootup"
date: 2007-03-31
forum: General Help
---

### Post by eklypze on 2007-03-31
Everything was fine when I installed Ubuntu 6.10 on my computer, there was absolutely no issues. Then I went out to buy a new video card (ATI Radeon x1600 AGP) and when I tried to boot up Ubuntu 6.10 again, the screen froze where the Ubuntu logo is and theres a progress bar, it froze right at the end. Beneath that progress bar there is a messed up bar of color green and blue, leading me to think that my new video card was the problem.

I did a bit of a Google search on how to fix this, adjusted my AGP speed from 8x to 4x in Catalyst Control Center on Windows XP (my BIOS doesnt have a setting to adjust AGP speed), rebooted and Ubuntu still didn't work.

My computer specs:
Intel Pentium 4 2.8GHz HT
1GB Memory DDR
ATI Radeon x1600 AGP 512MB 8x AGP
Dual Boot Windows XP/Ubuntu 6.10

Does anyone have any suggestions?

---

### Post by smokey edgy on 2007-03-31
Have you tried fetching the drivers? Here is a resource that may help you:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I had similar issues with my ATI x1950. The above guide helped remedy the problems I was having. I would suggest making sure you have all the latest updates before doing this. A certain version of the restricted modules was giving me grief.

---

### Post by r4ik on 2007-03-31
[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

Good luck !

---

### Post by eklypze on 2007-03-31
Thanks for the help guys. Apparently I just needed to get the drivers and remove the nVidia ones I had from before. Works perfectly now. :)

---

