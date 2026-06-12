---
title: "ubuntuguide.org homepage crashes and restarts X"
date: 2008-05-17
forum: General Help
---

### Post by meborc on 2008-05-17
trying to help some people at absolute beginner section i ofter refer to [www.ubuntuguide.org](www.ubuntuguide.org) ... easy and simple page with a lot of "tips" on how to install stuff on ubuntu

today, trying to access the page with firefox restarts my X ... does this happen to you too?

:confused:

---

### Post by perce on 2008-05-17
No it doesn't

---

### Post by b3n87 on 2008-05-17
mine does that!

---

### Post by b3n87 on 2008-05-17
and it still does it, i just checked. how random :S

---

### Post by Mazza558 on 2008-05-17
Same here.

---

### Post by Swarms on 2008-05-17
Same here.
Why is it even possible for a webpage to interfere with my xsession?

---

### Post by boomtisk on 2008-05-17
No crashing for me, running Hardy. Maybe the X crashing is related to Flash?

> **Swarms said:**
> Same here.
Why is it even possible for a webpage to interfere with my xsession?
In my experience, X likes to crash when there's a graphics card driver-related problem. I really doubt this is some kind of security issue.

Out of curiousity: what graphics card/driver are you guys using? I have an nVidia card and I'm using the "restricted" driver Hardy suggested to me.

---

### Post by FuturePilot on 2008-05-17
This is the same bug that causes pink or randomly colored shadows in Compiz for some people. It's also unique to the Nvidia 8 series cards. It has to do with an incorrect symlink in the nvidia-glx-new package.
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/212648]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/212648")

---

### Post by meborc on 2008-05-17
sys specs:

dell inspiron 1520 with nvidia 8600m gt

running hardy with latest updates... adobe flash and restricted drivers suggested by hardy...

x restarts every time i go to ubuntuguide.org

btw - compiz NOT enabled

---

### Post by Vicfred on 2008-05-17
My system was restarting X on that page too but for some reason it just stopped >_< and yep I'm using a nvidia 8 series (XFX 8800 GS XXX)

---

### Post by Swarms on 2008-05-17
Nvidia 8400M here. :)

---

### Post by zmjjmz on 2008-05-17
It didn't crash X in Kazehakase ;D

---

### Post by Mazza558 on 2008-05-17
I have an ATi card and it crashed me... ;)

---

### Post by spupy on 2008-05-17
Crashed X with Firefox 3beta5 with ATi card (radeon driver) on Gentoo! 

Looking at /var/log/Xorg.8.log (might be a different number), the backtrace from the crash starts at something about fonts. I would test it with another browsers (epiphany gtk and epiphany webkit), but i have proxy only for firefox.

---

### Post by boomtisk on 2008-05-18
Right, I guess a font-related problem would make sense, too. Maybe the site expects you to have the MS core fonts installed? That'd be slightly strange behaviour for a Linux site, though. :D

I do have them installed, though, lots of sites I visit and Firefox 3 b5's drop down menu look too weird if I don't have them.

---

### Post by meborc on 2008-05-18
tried epiphany... no surprise - x restarts... i guess it is related to the bug posted earlier... but why would some people with ati cards then have the same problem?

totally weird :)

---

### Post by _sAm_ on 2008-05-18
Same here, I have asked about it here in the forumes; [http://ubuntuforums.org/showthread.php?t=788253](http://ubuntuforums.org/showthread.php?t=788253)

I have nVidia 8800GTS and use compiz. Btw. Firefox on Ubuntu 8.04 crashes a lot, looking forward to the upgrade. 

I don't know if its relevant, but if I move/drag a lots of files in Nautilus it can also from time to time restart X, so I would need to log in again. 

Cant belive this is a LTS!

---

### Post by K.Mandla on 2008-05-18
Moved to General Help.

---

### Post by kalpik on 2008-05-18
Crashing X for me too.. Nvidia 8600 GT with nvidia-glx-new.. VERY strange!

---

### Post by kalpik on 2008-05-18
I can confirm this works: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/212648/comments/27](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/212648/comments/27)

```

sudo ln -sf /usr/lib/nvidia/libwfb.so.xserver-xorg-core /usr/lib/xorg/modules/libwfb.so

```

---

### Post by frodon on 2008-05-18
Any of you filled a launchpad bug report ?

Could be useful to inform devs of this.

---

### Post by spupy on 2008-05-18
How can this be a Nvidia bug if it crashes some ATi cards, too? Btw, Epiphany doesn't crash X, only Firefox.

---

### Post by kalpik on 2008-05-18
> **spupy said:**
> How can this be a Nvidia bug if it crashes some ATi cards, too? Btw, Epiphany doesn't crash X, only Firefox.
Maybe its the same packaging mistake in the ATi drivers that's in the Nvidia drivers.

---

### Post by zeny on 2008-05-20
Same here! It crashs with Dual monitors going! Nvidia 8800 GTS

---

### Post by heggel on 2008-05-25
Same here.
dell 1420n, hardy, nvidia card.
Turning on/off widgets, cairo-dock, compiz...nothing makes any difference.

---

