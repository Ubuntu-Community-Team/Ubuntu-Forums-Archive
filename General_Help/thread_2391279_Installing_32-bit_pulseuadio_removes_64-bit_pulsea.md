---
title: "Installing 32-bit pulseuadio removes 64-bit pulseaudio and vice-versa"
date: 2018-05-08
forum: General Help
---

### Post by thenailedone on 2018-05-08
Greetings all,

So I recently installed pulseaudio:i386 on Kubuntu 18.04 to run a wine-wrapped game. But when I did it removed pulseaudio (64-bit). And when I re-install pulseaudio it removes pulseaudio:i386. Why? And more importantly how to stop this shenanigans ):P

edit: An update, earlier today I launched the game and I had sound without having the 32-bit version of pulseaudio installed?! Due to time constraints I didn't do any more troubleshooting and still need to do a few reboots and launches to see how it performs.

---

### Post by Xian on 2018-05-08
> **thenailedone said:**
> Why? And more importantly how to stop this shenanigans 

In short the system is trying to save you from yourself. #-o

You should not install the same package with 32 and 64 bit versions. 

Why? 

They likely contain some of the same files. Multi-arch doesn't enable support for cross-compilation.

---

### Post by Yellow Pasque on 2018-05-09
You don't need to have the 32-bit version of pulseaudio. What you need is libpulse0:i386 and wine should pull this in automatically.

---

### Post by thenailedone on 2018-05-09
> **Xian said:**
> In short the system is trying to save you from yourself. #-o

You should not install the same package with 32 and 64 bit versions. 

Why? 

They likely contain some of the same files. Multi-arch doesn't enable support for cross-compilation.

Well I often have both the 64-bit and the 32-bit versions of files on my system. Install Steam and see how many 32-bit files it installs.

From [https://wiki.debian.org/Multiarch/HOWTO]("https://wiki.debian.org/Multiarch/HOWTO")
> Multiarch lets you install library packages from multiple architectures on the same machine. This is useful in various ways, but the most common is installing both 64 and 32-bit software on the same machine and having dependencies correctly resolved automatically. 

> **Temüjin said:**
> You don't need to have the 32-bit version of pulseaudio. What you need is libpulse0:i386 and wine should pull this in automatically.

I have not installed wine. The game is EVE-Online and it has a custom Wine wrapper. Anyhow, so far I still seem to have sound (could have been after I enabled multiarch that the problem resolved itself?!)

---

