---
title: "2 problems appeared after installing Lubuntu"
date: 2016-09-07
forum: General Help
---

### Post by den4ik1996 on 2016-09-07
Hello to everyone.

So, I have been using Ubuntu on my PC, and now I decided to install Lubuntu to my laptop (previously, I had Win7, and now Lubuntu 14.04 64-bit is the only OS installed, so I can't switch back to Win7) . So, I did it and it is working just fine except these 2 problems:

1)Screen ripples (like horizontal waves) appeared on my screen while playing videos or scrolling. I can't really ignore it, cause I have sensitive eyes and it disturbs a lot causing the eye-pain. It needs to be said that before installing Lubuntu I tried Ubuntu on my laptop, and it was fine. Didn't notice anything like that and had no problems with watching videos on Ubuntu.

2)My battery stopped charging (it stuck at 0%). So, the laptop is not working if the AC cord is not plugged in. It wasn't charging when I had Ubuntu either, but it was fine when I had Windows 7.

I would appreciate any help. Thanks in advance.

---

### Post by sudodus on 2016-09-07
Welcome to the Ubuntu Forums :-)

The more we know about the computer, the better advice you get. So please specify your computer

- Brand name and model
- CPU
- RAM (size)
- *graphics chip/card*, I think this is particularly important: brand name and model
- wifi chip/card

I suspect that there are problems with the graphics, and there are solutions, but we must know your graphics chip/card.

The battery problem might be solved with the new version of Lubuntu 16.04.1 LTS.

-o-

How is the graphics, when you run a live session, booted from your Lubuntu install CD/DVD/USB drive? Do you get the ripples also when running live?

---

### Post by den4ik1996 on 2016-09-07
1. Laptop - COMPAQ Presario CQ57
2. Processor - 2x Intel(R) Celeron (R) CPU B815 @ 1.60GHz
3. Memory - 2 GB
4.  description: VGA compatible controller       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
5. AR9485 Wireless Network Adapter

Ok, I will try to upgrade to Lubuntu 16.04 to check whether the battery problem will be solved or not.

What do you mean by a live session? Trying Lubuntu without installation?

---

### Post by sudodus on 2016-09-07
Yes, 'Try Lubuntu without installation".

See this link and links from it for more details: [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](https://ubuntuforums.org/showthread.php?t=2230389).

-o-

With Intel graphics it *should* work with Lubuntu 14.04.x LTS as well as with 16.04.1 LTS. *So for both issues it is worthwhile to try 16.04.1 LTS*, which is two years newer. You can also try *Ubuntu MATE* and *Xubuntu* (version 16.04.1 LTS). Most of the program packages under the hood are the same in all flavours of Ubuntu, but there are differences, so they are worth trying.

Maybe it helps with *UXA acceleration*, but use it only if necessary to get rid of the ripples. See this link: [Lubuntu/AdvancedMethods#Old_Intel_graphics](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Old_Intel_graphics), but I found a link telling me that the processor was released in 2012, which is fairly new, so it should not be a candidate for 'tweaks to fix issues with old Intel graphics'.

***Edit:*** You wrote that Ubuntu works. Did you try the same version (14.04 LTS)? Or a different point release 14.04.x LTS than Lubuntu, where x is [1,2,3,4,5]. Why did you change to Lubuntu - because the video playing was lagging with Ubuntu, or for some other reason?

---

### Post by den4ik1996 on 2016-09-08
The graphics problem remains when I run a live session. 
And upgrading to Lubuntu 16.04 didn't resolve any of the issues.

The reason why I switched to Lubuntu and want to stay with it is that this OS is lightweight and fast while on Ubuntu my laptop was really slow. 

Alright, I will try UXA acceleration then.

---

### Post by den4ik1996 on 2016-09-08
UXA acceleration helped! Now the only problem I have is the battery that is not charging. Any ideas how I can fix it?

---

### Post by sudodus on 2016-09-08
I have never had problems with batteries not charging, except when the battery was worn out or broken (so would not work with Windows). I don't know, but let us invite other people who might know about charging batteries:

I suggest that you ***start a new thread with a good descriptive title*** (for example battery not charging). Describe as much as possible, for example copy part of the content of post #1 and all of post #3 from here to the first post of the new thread. You can add a link from here to the new thread if you wish. This way you will attract people who know about charging batteries.

---

### Post by den4ik1996 on 2016-09-08
Ok, thanks for your help. Here is the new thread:

[https://ubuntuforums.org/showthread.php?t=2336441&p=13541750#post13541750](https://ubuntuforums.org/showthread.php?t=2336441&p=13541750#post13541750)

---

### Post by sudodus on 2016-09-08
Good luck with the new thread :-)

---

