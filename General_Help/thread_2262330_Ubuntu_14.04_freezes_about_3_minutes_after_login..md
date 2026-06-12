---
title: "Ubuntu 14.04 freezes about 3 minutes after login."
date: 2015-01-24
forum: General Help
---

### Post by PotatoHead007 on 2015-01-24
Hi.

I have a very serious problem. When i boot Ubuntu 14.04,  everything works fine. For ~3 minutes, I can do everything i usually  can, like open Firefox etc. After that short time, the system freezes.  NOTHING works. Not even Ctrl+Alt+F1. keyboard, mouse and screen  unresponsive, justa frozen image. I have tried waiting, but i can only  force restart by pressing power button.
This issue just happened over  a day. It worked perfectly fine, then i shut my laptop down for a day.  Booted it up, and i had this problem. I did not install anything for  more than a week.

System specs:
i5 2.6 Ghz
4GB DDR3
nVidia M640
500GB HDD

Please help! I am enrolled in an online school and all my files are on there, and i need to do school, its my final year!

Any help deeply appreciated.

**Update: **The problem is that the laptop is overheating. I put it in a cool room until it was not even warm, then i turned it on. In a few minutes the laptop was so hot that it was sore to the touch. Any ideas as to why?

**[SIZE=4]Update#2: [/SIZE]**[SIZE=2]The overheating was fixed by installing indicator-cpufreq[/SIZE]:
```
sudo apt-get install indicator-cpufreq
```
and keeping it on "On demand"

---

### Post by QIII on 2015-01-24
Hello!

Is this a laptop or a desktop?

---

### Post by PotatoHead007 on 2015-01-24
It is a laptop, Samsung 3 series

---

### Post by PotatoHead007 on 2015-01-24
Fixed! See OP for more info.

---

### Post by Bucky Ball on 2015-01-24
Please mark the thread as solved using Thread Tools. Thanks.

---

