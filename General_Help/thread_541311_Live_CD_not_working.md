---
title: "Live CD not working"
date: 2007-09-02
forum: General Help
---

### Post by zajacattack on 2007-09-02
Hello, I just received my Ubuntu 7.04 CD. I tried to boot from it. I selected "Start or Install Ubuntu" at the boot menu. Then, the Ubuntu logo with a progress bar showed up for thirty seconds or so. Then, I started getting error messages. Every few minutes or so a new one would pop up. It would say:

Buffer I/O error in device hdc, logical block 0
hdc: device is not ready for command

Then, after a few minutes

Buffer I/O error in device hdc, logical block 1
hdc: device is not ready for command

Every few minutes a new error message comes up with the logical block being incremented by one. So, as you can see, my boot fails. I am running a PC with a Pentium 4 1.8 Ghz processor, 256 MB of RAM, and am booting from a CD-RW drive. Can someone help me get the live CD working? I just want to try Ubuntu, not install from the alternate desktop CD. Isn't there a boot option I can use?

---

### Post by banewman on 2007-09-02
This mostly works - at the "start or install ubuntu" screen - hit f6 - and at the boot prompt that appears type - noapic nolapic - and it should run the live cd.

---

### Post by zajacattack on 2007-09-04
It didn't work. Even with noapic and nolapic, I still have the same problem. Is there something else?

---

### Post by Bablefish on 2007-09-04
Strangely enough I had the exact same problem when I install Ubuntu All I did to fix it was wait....it took roughly 14 minutes to clear all by itself

---

### Post by zajacattack on 2007-09-04
So, I should just let it go? I'm not very patient, so I usually gave up after a few minutes. But, does that seriously work?

---

