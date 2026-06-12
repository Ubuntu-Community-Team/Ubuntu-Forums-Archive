---
title: "Ubuntu 12.04 (or newer) on a Raspberry Pi"
date: 2013-07-03
forum: General Help
---

### Post by SirDelder on 2013-07-03
Is it possible to put Ubuntu/Kubuntu 12.04, or later, on the raspberry pi?
I know that 9.04 would run, so could I pull its kernel out and put it in 12.04, or would that just screw things up?
If it would work please leave steps (I've only been using Ubuntu/Kubuntu for 4 Months and am still a nube).

---

### Post by CaptainMark on 2013-07-03
No, the Raspberry pi is barely powerful enough so if possible it would run really slowly and Ubuntu is not built for the right ARM architecture, it would take someone months of hard effort to compile it, which no one seems prepared to do because there are much better alternatives already out there

---

### Post by 3rdalbum on 2013-07-03
No, not possible without porting, but there are certain Android mini PCs that can run Ubuntu and are a lot faster than the Pi. Or you can use Raspbian, it's based on Ubuntu's parent distro Debian.

---

### Post by Dozy Van on 2013-07-03
raspbain is one that you can use. Its very small and like ubuntu is debain bassed. So you can "Sudo apt-get <anything>"


The problem is that even if it had the power Ubuntu has no support for ARM. So even with a cluster of 100 pi's you still wont be able to run ubuntu unless manually create support for ARM.

---

### Post by mastablasta on 2013-07-03
Ubutnu has support for ARM, but not for the old model of the CPU found in RPi

---

### Post by SirDelder on 2013-07-03
OK, I'll try to find some Distro that does run easily with KDE as the default GUI
Thanks though

---

### Post by CaptainMark on 2013-07-03
Bad idea, KDE is just too heavy duty for the Raspberry Pi. You'll burn the poor little thing out if you push it too hard. You'll have to use lightweight environments like LXDE, at a push you can run XFCE but it's a bit tediously slow. You can't expect to run the same setup as a modern computer on a computer that is comparable to a home desktop from about a decade ago.

---

