---
title: "Ubuntu 14.04 LTS and Ubuntu Web Browser (Browser)"
date: 2015-10-28
forum: General Help
---

### Post by fangorn2 on 2015-10-28
Hi,

for web development reasons I was looking for an alternative to Firefox when I realized that in my distribution (Ubuntu 14.04 LTS) there was another browser installed by default: Ubuntu Web Browser (named simply 'Browser' in Software Center).

To my disappointment this browser looks really bare bones a browser, with no menu bar whatsoever, so no possibility of any customisation, tab navigation not implemented and no possibility to open more than a window. Maybe it is still under development, I thought. 
 
However, after some research, I discovered that Ubuntu Web Browser is a very richer featured browser in Ubuntu 15.04 and Ubuntu 15.10. Look for instance at the following link: [https://www.youtube.com/watch?v=Xvyu3RftGUw](https://www.youtube.com/watch?v=Xvyu3RftGUw)

So I wonder why in Ubuntu 14.04 LTS Ubuntu Web Browser is so poor, and its use I would say not really inviting for any user, compared to its variant at the benefit of those using Ubuntu 15.04 and 15.10.

Is there any possibility to download, install and use the richer versions of this browser or will these be available in the near future also for Ubuntu 14.04 LTS?

Many thanks in advance

---

### Post by TheFu on 2015-10-29
Please make your web-apps work with **dillo**. 
Sure, some things won't work, but the basic functionality should **always** work on a plain web browser. Drives me crazy when webapps require javascript or flash to work.

Make me even happier and support **Lynx**.  ;)

Oh ... and *Software Center* is like training wheels on a bicycle. If you want to see all the packages available in the Canonical Repos  - use **apt-get**, **aptitude** or **synaptic**.  Synaptic is probably what you want.

I use dillo by default for security reasons and only use a heavy browser when mandatory - most websites that show up with a blank page I don't need to visit. It just isn't worth the risk.

---

### Post by grahammechanical on 2015-10-29
Ubuntu web browser (A.K.A. Browser) is the browser that comes pre-installed in Ubuntu Phone. And Ubuntu Phone is very much a "still under development" OS. And so is the goal of code convergence between Ubuntu running on PCs; Phones; Tablets and TVs.

The version of Browser is so poor, as you put it, in 14.04 because it is the Browser for Ubuntu phone. Over the last 18 months a lot of work has been done to "converge" phone apps to scale and work as desktop apps as part of the convergence story. And improvements to Ubuntu web browser on the desktop demonstrate the work being done. 

So, why are you not seeing this in Browser on 14.04? Have you upgraded to 14.04.3? That should bring 14.04 closer to 15.04. But to get closer to 15.10 you will need to upgrade to 14.04.4 when it is released some months from now. Although I cannot say if Browser in 14.04.3 is comparable to Browser in 15.04. 

Besides, the targets now for the desktop are 16.04 and Ubuntu Personal. Two visions for Ubuntu desktop that are so alike and yet so different. And it seems that it is Ubuntu Personal that is the target for convergence and not Ubuntu desktop 16.04.

It is Ubuntu development policy to bring improvements to Ubuntu through 6 monthly releases and to keep Long Term Support releases up to date, especially in regard to hardware drivers, though six monthly point releases that are out of phase by several months with the six monthly release pattern.

Regards.

---

### Post by fangorn2 on 2015-10-29
I probably directly installed Ubuntu 14.04.3, since I downloaded the iso image one month ago.
Anyway the command 'lsb_release -a' says I am on **Ubuntu 14.04.3 LTS**.
My Browser version is far from being any close to the versions for Ubuntu 15.04 or 15.10. Let's see if there will be any improvement with Ubuntu 14.04.4. At present it is unusable.

I will try **synaptic **for sure, it looks really interesting, hoping there will not be any conflict with Software Center.
I am afraid I have planned to use javascript, so I guess I will not install dillo. Not sure about lynx, since I made use of it years ago, when my distro was Slackware, and liked it.

Many thanks for your help

---

### Post by TheFu on 2015-10-29
The package manager on Ubuntu is "APT" - those tools I listed are front-ends to APT. No worries. They all are fine together, though aptitude tends to be the smartest for complex dependency issues.

---

