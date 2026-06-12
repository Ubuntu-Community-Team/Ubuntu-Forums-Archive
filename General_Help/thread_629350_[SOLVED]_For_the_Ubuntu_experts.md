---
title: "[SOLVED] For the Ubuntu experts"
date: 2007-12-02
forum: General Help
---

### Post by dracker on 2007-12-02
Hi, my suspend and hybernate doesn't work so I decided to google it, I found this as an option to fix it:

[http://blog.vaxius.net/?p=19](http://blog.vaxius.net/?p=19)

Since I'm new in Ubuntu and right now my configuration is almost the way I like can you please tell me what I'm going to lose doing that?.
If you know how to fix Suspend in a easer way I'll be very thankful too. 
My configuration is:

AMD + Ati Radeon Xpress 1100 + fglrx + ubuntu Gutsy

I don't want to lose Compiz, Wireless and in general all my software, my data is protected.
Thank you for your help!

---

### Post by climatewarrior on 2007-12-02
I dont know if there is any other solution but I dont recommend that solution since you have to change the kernel and that might bring an array of new problems.

---

### Post by XVII on 2007-12-02
That looks pretty involved & you might mess something up but if you're confident, go for it.

---

### Post by dracker on 2007-12-04
I'll do it in a few days, after the end of semester.
I'll come back with the experience.

---

### Post by lswest on 2007-12-04
alright, but typically i think just shutting off your laptop isnt that bad with linux, as start up times are a joke:P but then again my suspend works:P  good luck with the reverting of the kernel! *gives thumbs up*

---

### Post by metalheart on 2007-12-04
If you can give up the fglrx/3D, radeonhd drivers work well (see [http://wiki.x.org/wiki/radeonhd](http://wiki.x.org/wiki/radeonhd) for limitations). I can suspend/hibernate my Radeon X1400 laptop.

---

### Post by dracker on 2007-12-16
Here are my experiences:
1) I made a fresh install of Feisty (since is said that this kernel is supported to suspend) and upgraded it to Gutsy with the update manager, once there I activated the ATI restricted driver from the manager and my suspend and hibernation worked perfectly, other problems showed, especially when installing some apps, the problem was that I had to use the old kernel with Gutsy and some apps complain about a version mismatch and refused to install, and of course, some hardware issues showed too since the kernel was out of date.
2) I compiled a custom kernel using [this instructions]("http://blog.vaxius.net/?p=19"), it wasn't difficult but some of the steps I had to figure out, there is when you need to know what you're doing, I managed to reboot perfectly after and see my gutsy, everything was going fine until I tried to activate the ATI restricted driver, the "restricted driver manager" refused to start since "it wasn't supported by my kernel", also a lot of stuff didn't worked for the same issue, when I couldn't get anything to work as I liked I gave up.

The conclusion: I prefer eye candy over the suspend feature, the thing is that if you don't activate the ATI's restricted driver then you'll being using the normal radeon driver and suspend and hibernation will work perfectly, you can even get compiz if you're lucky and have a supported card.
Anyway it is said that ATI's driver will soon support the Gutsy new kernel (It was supposed to be included in the 7.11 driver) and also will become open source, I'm actually waiting for Hardy since I have the feeling everything will work perfectly for me with it... a long wait until April but I'll finally get to uninstall completely Windows! (the only thing that is there for are because I can't get full 2007 office's document support and I wasn't able to make a presentation with Gutsy).
Hope somebody find this useful  :)

---

