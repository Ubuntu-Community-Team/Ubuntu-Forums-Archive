---
title: "Upgrade to 16.04: External Monitor Flicker/Black Screen"
date: 2016-08-06
forum: General Help
---

### Post by jonathan1985 on 2016-08-06
Hello,

I updated my Ubuntu 14.04 to 16.04 LTS, and I have since had some issues with my external monitor. As I move my cursor to my second monitor I often get screen flicker, a brief black flash, it also flickers on my primary laptop screen when I do this. The flicker is relatively inconsistent, it happens more often than not though. Most frustratingly of all is that quite often my external monitor will go fully black and I will need to click on that screen or move the cursor to it to see the screen properly again. I had none of these problems with Ubuntu 14.04 and I now regret upgrading. I have looked at rollback options but I would much rather avoid this. Has anyone else experiences this? is it an issue with the compatibility of my graphics and Ub 16.04?

I'm using:

Lenovo ThinkPad T140s laptop
    -Ubuntu 16.04 LTS
    -processor: intel Core I5 CPU M 520@2,40GHz x 4
    -graphics: Ironlake Mobile
    -OS type: 64bit
    -VGA compatible controller: Intel Core Processor Integrated Graphics Controller (rev 02) (prof-if 00 [VGA controller])

Cheers,
Jon

---

### Post by howefield on 2016-08-07
Moved by request to the "*General Help*" forum.

---

### Post by fwendt on 2016-08-24
Yes. I have similar setup T410 and I too experience this. Haven't found a proper bug report, but I can reproduce this easily by moving focus between two terminal windows on different monitors (both external), and after switching focus typing any key on the keyboard will trigger this nasty regression/bug.

---

