---
title: "Everything Slows Down When Typing"
date: 2021-04-04
forum: General Help
---

### Post by mccoo8884 on 2021-04-04
Hello,

I've installed Ubuntu 20.04.2.0 and it runs fine, except for one thing. Everything slows down when I type, and it is extremely noticeable when I press the spacebar and backspace really fast. Everything freezes and I can hear my PC fans spinning faster. Everything just freezes for some reason. I am a fast typer and when I'm trying to type messages on Discord or anything it's also noticeable. I've recorded a video:

[https://www.youtube.com/watch?v=xvectst_STU](https://www.youtube.com/watch?v=xvectst_STU)


I type in some gibberish slowly and that goes fine. Then I start mashing backspace and spacebar and everything just completely freezes until I give it less inputs. At the end I hold backspace and it does not unfreeze until I let it go. Any ideas?

Specs:
GTX 970
i7-4790k
8GB
Z97x Gaming 3

Thanks in advance.

---

### Post by CelticWarrior on 2021-04-04
Are you using the proprietary Nvidia drivers or the open-source nouveau?

---

### Post by vanadium on 2021-04-04
Perhaps also do the following to help identifying the cause. Run "top" in a terminal, right-click the titlebar to keep it on top. Do your typing test and you will see which processes are starting to use the CPU.

---

### Post by HermanAB on 2021-04-04
Maybe the NSA key logger infrastructure is a bit overloaded?
&#128514;

---

### Post by mccoo8884 on 2021-04-08
> **vanadium said:**
> Perhaps also do the following to help identifying the cause. Run "top" in a terminal, right-click the titlebar to keep it on top. Do your typing test and you will see which processes are starting to use the CPU.

Hello,

The Xorg commands shoots up to 90% and higher right after my PC stops freezing. I've plugged in another keyboard and I am able to type fine with that. I would really like to use this keyboard though.

---

