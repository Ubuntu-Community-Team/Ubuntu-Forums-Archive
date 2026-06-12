---
title: "Kubuntu 12.04.3, Nvidia PCI-E card AND Intel IGD at the same time?"
date: 2013-09-07
forum: General Help
---

### Post by djyoshabyd2 on 2013-09-07
Hey, everyone. 

So I recently built a system with the following specs:

MSI B75a-G43
Intel i3 with integrated graphics (HD 3000, I believe)
Nvidia GT 640


So, I know I can run 3 monitors from my GT 640, but I am actually trying to use the integrated graphics WITH the Nvidia at the same time. Almost like what Bumblee/optimus and all that does. Now, KEEP IN MIND, this is NOT a laptop. Its a desktop. I have been searching for days and no matter how I search, I keep coming up with stuff for laptops and this situation but not for a desktop with an IGD and nvidia card.

I have tried HWE versions of different kernels, different versions of the proprietary nvidia driver, different versions of X, etc etc etc.. Kubuntu sees the Intel card, and shows that the i915 module is assigned to it, as well as seeing the nvidia card.

The Nvidia card works just fine, but the monitor hooked up to the onboard IGD does not turn on. lspci, lshw, etc. all show the card, but Kubuntu gives me no options to adjust or do anything. Just for the Nvidia card.

Any ideas? I have upgraded the BIOS as well, and made sure that multimonitor support is turned on, and BOTH IGD and the Nvidia card are on in the BIOS. 

Im so lost. I usually have great Google-fu, but yeah. Any suggestions?

---

### Post by djyoshabyd2 on 2013-09-07
Oh, and I forgot to add; Yes. It works just fine in Windows, so I know the hardware can do this. Im just not sure what software/kernel/libs I need to enable it in linux.

---

### Post by djyoshabyd2 on 2013-09-08
So, after working on it some more, and building a bleeding-edge arch setup, I can get all 3 monitors to light up, but I cannot get the 3rd monitor (on the integrated card) to let windows move between them. Graphics acceleration is active on all screens, just need to find a way to merge them. 

Anyone have any clue how to do a minimal xorg.conf configuration JUST so xrandr will see both cards and I can merge them onto 1 X screen?

[xineramaglx.html]("http://us.download.nvidia.com/XFree86/Linux-x86/319.32/README/xineramaglx.html")

^^^^^On this page, I read that Nviidia drivers support Xinerama with GLX, but I remember losing MANY MANY nights of sleep trying to get this to work across 2 nvidia cards with 3 monitors, and whenever xinerama is enabled, GLX/Composite is off. But the official docs say it works...

Any suggestions would be greatly appreciated... Like, ANY suggestions. Just start lobbing them in here. Id hate to see this post go unanswered for weeks like some of my other ones. hahaha. :)

EDIT: Dude....150+ views, and not a soul even has a clue? hahahaha. really?

---

### Post by djyoshabyd2 on 2013-09-08
I was also thinking about Base Mosaic. I have the GT 640 that Im trying to use now, but I also have an 8600 GT PCIE card. Perhaps I will have better success running base mosaic? From what I have read, it should span 1 X screen over 2 cards without needing an SLI bridge. 

Anyone have luck with this?

Im going to keep posting my findings and what Im going to try and whatnot, so hopefully someone will actually attempt to help troubleshoot this. I have been reading my a$$ off, and everything is SUPER outdated with useless info. 

So, cmon guys. Start tossing in some suggestions. No one is even trying. Is this too hard? hahaha. I see all of these easy questions being handled super fast, but is this complicated xorg config scaring youse? :)

---

### Post by djyoshabyd2 on 2013-09-08
Tried to just use the device section for each card ONLY, with just one X screen defined in xorg.conf, and even though the nvidia card displayed the 2 monitors hooked up on the card on screen 0, the intel card would not be picked up by xrandr.

Im using:

Linux kernel 3.10.11
Xorg 1.14
KDE 4.11
xrandr 1.4
nvidia driver 325.08 (whatever is the newest beta available)

---

### Post by djyoshabyd2 on 2013-09-08
Lol. This happens every time I ask a non-routine question in these forums. Seems like I tend to stump everyone, including the old-hands? :D

---

### Post by djyoshabyd2 on 2013-09-08
Anyone besides straight-up Linux n00bs that wants to troubleshoot a difficult issue, instead of giving cookie-cutter answers to the most basic linux issues? I know there has to be people interested, given the amount of views.....

---

### Post by djyoshabyd2 on 2013-09-08
nvrmind. Ill find answers elsewhere.

---

