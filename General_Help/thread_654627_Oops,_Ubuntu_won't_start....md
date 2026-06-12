---
title: "Oops, Ubuntu won't start..."
date: 2007-12-31
forum: General Help
---

### Post by Zacha on 2007-12-31
Well.
To make a long story short I tried to install the iwl3945 driver (and therefore tried to install the mac80211 package) and now my ubuntu won't start as it should (X boots into safe mode and my touchpad won't work).

Before I restarted (shut down for the day) the mac80211 package complained on my makes (and therefore I thought nothing happened).

Any help how to begin troubleshooting would be welcome. Or maybe if I should try a whole new install (I haven't done that much to it yet, It's the second choice of my dualboot laptop, mostly for familiarizing with linux)

---

### Post by p_quarles on 2007-12-31
How were you trying to install this driver? My laptop has an Intel Pro 3945, and all it needs is the restricted module, which should have been configured automatically by the installation disk. There's no need to manually install the Intel driver. If it didn't autoconfigure, it should still be easy to get it up and running.

---

### Post by Zacha on 2007-12-31
> **p_quarles said:**
> How were you trying to install this driver? My laptop has an Intel Pro 3945, and all it needs is the restricted module, which should have been configured automatically by the installation disk. There's no need to manually install the Intel driver. If it didn't autoconfigure, it should still be easy to get it up and running.

Well. What I've understood the iwl3945 driver works better (and is easier to configure so it doesn't die when the laptop is suspended and started once again).

Well. As I said the computer didn't want to install (or more correctly make the kernel patch) as described [here]("http://www.intellinuxwireless.org/index.php?p=mac80211&n=HOWTO-mac80211"). And next time i tried to start it up again it complains of something (I think it's the wireless card) and blinks sometimes before going into safemode.

So if it's possible to remove this kernel patch (whatever that is =P) it would be helpful ;)

EDIT: And before anyone says "If you are a beginner you shouldn't do things like that" I'd like to repeat that this was the second choice OS and I had it to do things like this, i.e. try it and configure it until it broke =P

---

### Post by p_quarles on 2007-12-31
I can't say I've had any problems like that with the restricted module. The connection persists through suspends and X server restarts.

Anyway, I believe that you should be able to simply reinstall the kernel you initially used when setting up. Please note that kernel stuff is *not* an area I'm terribly knowledgeable about, so I'm providing this with the understanding that you're a) willing to break stuff, and b) willing to reinstall if need be. ;)

That caveat aside, I'm fairly certain this will work, since many people have complained about kernel updates overriding their customized modules. What I'm suggesting is essentially the same thing, except you'd be reinstalling the old kernel rather than installing a new one.

Anyway, you'll first need to obtain the specific version of your kernel, which you can do by running:
```
ls /boot
```

---

### Post by Zacha on 2008-01-01
Further update/clarifications.

The computer boots into low graphics mode, not "safe mode" as I said.
Secondly it's the hardware drivers that doesn't work (I guess). This probably causes the low graphic mode. It's also kinda obvious as the wlan card and touchpad doesn't work (and bluetooth I guess, can't see the icon).
When booting everyting goes fine until the end of the progressbar (starting X?) where the screen switch between black screen and boot info (just some OK's except that it fails to load binfmt_misc.ko, I guess that's for FAT32 mounting as I can't access my FAT partition) before going into low graphics mode.

My kernel is 2.6.22-14-generic (as get from ls /boot directories and uname -r)

Oh, and while trying to install the mac module I _think_ I downloaded the source for the kernel (the header files I already had).

---

### Post by p_quarles on 2008-01-01
> **Zacha said:**
> Further update/clarifications.

The computer boots into low graphics mode, not "safe mode" as I said.
Secondly it's the hardware drivers that doesn't work (I guess). This probably causes the low graphic mode. It's also kinda obvious as the wlan card and touchpad doesn't work (and bluetooth I guess, can't see the icon).
When booting everyting goes fine until the end of the progressbar (starting X?) where the screen switch between black screen and boot info (just some OK's except that it fails to load binfmt_misc.ko, I guess that's for FAT32 mounting as I can't access my FAT partition) before going into low graphics mode.

My kernel is 2.6.22-14-generic (as get from ls /boot directories and uname -r)

Oh, and while trying to install the mac module I _think_ I downloaded the source for the kernel (the header files I already had).
So, it sounds like this could be more of an Xorg problem, rather than a kernel problem. You could first try reconfiguring that:
```
sudo dpkg-reconfigure xserver-xorg
```
If you still think it could be a kernel problem, though, you could try reinstalling that:
```
sudo dpkg-reconfigure linux-generic
```

---

### Post by Zacha on 2008-01-02
Hmm, neither worked.
The first one sent me through a "wizard" (where I mostly pushed enter).

The second command did nothing (at least it did seem so), no error, no status.

---

### Post by Zacha on 2008-01-03
Sorry for the double post but if anyone could point me in the right direction I'd be glad

To put it short, my hardware have stop working, the "generic monitor" at 1280x1024, my keyboard and my mouse is the only thing working.
This after a try to make a kernel patch and _maybe_ also a ubuntu update

(if it changes everything I compiled my old xorg myself without some unused function that would have borked my graphic card when using EXA or something).

---

### Post by Zacha on 2008-01-09
Ok, I know. Triple post. But I would like some help, or as I said just pointers would be nice.
Like if anyone could tell me if ubuntu have any repair feature.
Or if anyone could tell me how to get a better "log" or vocal startup so I can see where it goes wrong.

---

### Post by Zacha on 2008-01-16
Wee. Quadruple post!

For the last time, if anyone can help me or give me some pointers I would be REALLY thankful.
Plus it would be really helpful for me...

And if I need to blow the whole installation tell me so and I'll maybe reinstall it...

Thank you for answering and helping.

---

### Post by Zacha on 2008-01-26
Well.

Thank you p_charles.

No thank you to you others of the "helpful ubuntu community".

I guess this was as far I could play with my ubuntu installation before breaking it and getting no help at all.
Maybe I'll return one day when I'll need a linux installation and/or some unix experience.
Because ATM I don't feel like reinstalling everything and maybe cause a breakage again (because I don't really know what went wrong).

Keep up the good work (you developers I mean then, because supportwise I've only been dissapointed so far, have had about 3 problems, the forum have never answered them).

Wellwell, bye!

---

