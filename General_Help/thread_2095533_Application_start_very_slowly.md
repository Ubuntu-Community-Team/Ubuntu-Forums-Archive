---
title: "Application start very slowly"
date: 2012-12-17
forum: General Help
---

### Post by lordfkiller on 2012-12-17
I'm running Ubuntu 12.10 with GNOME 3 (although the situation was no different with Unity). Starting application takes a long time for the first time (starting chrome can take up to 10 seconds whereas it takes much less in Windows 8 on the same machine).
Desktop effects are slow also. E.g. when I activate activity panel the transition is slow at first, but if I do it again immediately it will be smoother.

Is there anything I can do about that? Does installing Ubuntu on my first partition help make it faster? (it's already on a primary partition, but the first primary partition is occupied by useless Windows 8)

System specs: Intel Core i7 CPU M 620 @ 2.67GHz × 4

---

### Post by Hungry Man on 2012-12-17
What GPU do you have? Hard drive? Is this a fairly fresh install or have you installed many programs?

Slowness can be caused by a lot of stuff, it's good to get as much info as possible.

---

### Post by Pjotr123 on 2012-12-17
You can supply the needed info as follows:
[https://sites.google.com/site/easylinuxtipsproject/tips#TOC-Make-automatically-a-nice-document-with-all-your-hardware-information](https://sites.google.com/site/easylinuxtipsproject/tips#TOC-Make-automatically-a-nice-document-with-all-your-hardware-information)

Apart from "deep probing" this buggy behaviour, you might try if installing new microcode helps, too:
[https://sites.google.com/site/easylinuxtipsproject/microcode](https://sites.google.com/site/easylinuxtipsproject/microcode)

Installing new microcode should be quite safe, without any negative side effects whatsoever.

---

### Post by lordfkiller on 2012-12-17
> **Pjotr123 said:**
> You can supply the needed info as follows:
[https://sites.google.com/site/easylinuxtipsproject/tips#TOC-Make-automatically-a-nice-document-with-all-your-hardware-information](https://sites.google.com/site/easylinuxtipsproject/tips#TOC-Make-automatically-a-nice-document-with-all-your-hardware-information)

Apart from "deep probing" this buggy behaviour, you might try if installing new microcode helps, too:
[https://sites.google.com/site/easylinuxtipsproject/microcode](https://sites.google.com/site/easylinuxtipsproject/microcode)

Installing new microcode should be quite safe, without any negative side effects whatsoever.

 There you go. It seems that I am not running Ubuntu on a primary partition.
It is an almost fresh install. I have added a few application like Skype and NetBeans

---

### Post by Pjotr123 on 2012-12-17
Is your Nvidia card running on the restricted driver? If not, install the restricted driver:
[https://sites.google.com/site/easylinuxtipsproject/first#TOC-Make-sure-all-hardware-is-working-properly-and-install-missing-drivers](https://sites.google.com/site/easylinuxtipsproject/first#TOC-Make-sure-all-hardware-is-working-properly-and-install-missing-drivers)

Primary or logical partition doesn't matter. That has no effect at all on the performance.

---

### Post by offgridguy on 2012-12-17
> **lordfkiller said:**
> I'm running Ubuntu 12.10 with GNOME 3 (although the situation was no different with Unity). Starting application takes a long time for the first time (starting chrome can take up to 10 seconds whereas it takes much less in Windows 8 on the same machine).
Desktop effects are slow also. E.g. when I activate activity panel the transition is slow at first, but if I do it again immediately it will be smoother.

Is there anything I can do about that? Does installing Ubuntu on my first partition help make it faster? (it's already on a primary partition, but the first primary partition is occupied by useless Windows 8)

System specs: Intel Core i7 CPU M 620 @ 2.67GHz × 4
I have read a few threads since 12.10 came out relating to it's slowness,
if i find one i will post a link to it.:p

---

### Post by lordfkiller on 2012-12-18
> **Pjotr123 said:**
> Is your Nvidia card running on the restricted driver? If not, install the restricted driver:
[https://sites.google.com/site/easylinuxtipsproject/first#TOC-Make-sure-all-hardware-is-working-properly-and-install-missing-drivers](https://sites.google.com/site/easylinuxtipsproject/first#TOC-Make-sure-all-hardware-is-working-properly-and-install-missing-drivers)

Primary or logical partition doesn't matter. That has no effect at all on the performance.

Yes I am running Nvidia's own driver. Although the driver on repos didn't work for me, I downloaded from Nvidia website directly.
Installing the driver made OS start-up slower. I think a couple of errors happen once I login. Ubuntu splash screen disappeared too.

---

### Post by Pjotr123 on 2012-12-18
Does the performance improve when you use this other desktop:
[https://sites.google.com/site/easylinuxtipsproject/alternative](https://sites.google.com/site/easylinuxtipsproject/alternative)

---

### Post by lordfkiller on 2012-12-28
Okay. I installed a fresh Ubuntu as my system was so unstable after installing and removing Unity and GNOME Shell several times.

The problem with slow  (first time only) application start-up remains and it seems to be independent of the desktop environment used. 

But slow desktop effects had a different cause: NVIDIA PowerMizer. With PowerMizer, GPU clocks go to level 0 (almost 1/5 of the max clock frequency for my card) when there is no graphics intensive app running. So when I activate Activities menu, the effects are not smooth the first time. It then jumps to level 2(max) and all 3D effects start working. But within a minute or so it goes back to level 0 and so on.

Here's how I disabled PowerMizer: [http://askubuntu.com/questions/232572/how-to-get-rid-of-nvidia-powermizer](http://askubuntu.com/questions/232572/how-to-get-rid-of-nvidia-powermizer)

Update: I changed my driver to the latest experimental NVIDIA driver and 3D effects work much better now - no bugs or issues so far

---

