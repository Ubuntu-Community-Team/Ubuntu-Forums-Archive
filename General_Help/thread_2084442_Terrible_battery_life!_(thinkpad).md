---
title: "Terrible battery life! (thinkpad)"
date: 2012-11-15
forum: General Help
---

### Post by gabbi on 2012-11-15
Hi there!

I'm a Lenovo Thinkpad X1 owner. I was using Linux Mint 13 for a few months, but a few days ago, I decided to switch to Xubuntu 12.10. Of course, I expected better battery life and less power consumption, because of XFCE. Unfortunately, things went terrible and now, the power consumption in IDLE is between 20-30W!!! While using Linux Mint, the consumption was 8-9W on average. I think I tried everything possible, for example [http://29a.ch/2011/10/14/review:-ubuntu-linux-on-thinkpad-x1](http://29a.ch/2011/10/14/review:-ubuntu-linux-on-thinkpad-x1) but nothing helps. I'm really disappointed and I have no idea what to do next. Battery life is very important for me. 

Please, could anybody help me? Even if a guess, what could be the problem.

Thanks a lot.

---

### Post by Impavidus on 2012-11-15
First thought is it could be your graphics card. If you don't have the correct driver it might be stuck at maximum performance (and maximum power consumption). This often happens after installation, the way to solve depends a bit on what graphics card you have. Otherwise, check your CPU frequency (it should go down when the CPU is idle). The other big power consumers (wifi, screen backlight, hard disk) are unlikely to be influenced by your new OS.

---

### Post by gabbi on 2012-11-15
Actually, my GPU is integrated on my CPU. Do I need to install any drivers for it?

---

### Post by Impavidus on 2012-11-15
Usually not, but I'm not an expert on that.

---

### Post by GreatDanton on 2012-11-15
I am not sure about Gpu but you can see if there are any drivers available under Software sources / Additional Drivers tab.

I would try to improve battery life with [Jupiter applet]("http://www.jupiterapplet.org/").

Hope this helps.

---

### Post by gabbi on 2012-11-15
Software sources haven't found any other drivers to install.

Maybe I could try the Jupiter applet, but I have negative experience with it. 

Anyway, thanks for replies.

Any other suggestions?

---

### Post by gabbi on 2012-11-16
Jupiter app = no result

Actually, powertop shows about 400 CPU wakeups per second and about 100 CPU wakeups per second in IDLE. Isn't it the core of the issue?

---

