---
title: "Possible fix for slow Feisty 7.04"
date: 2007-05-22
forum: General Help
---

### Post by atze76 on 2007-05-22
all the feisty 7.04 users who have bad experience with feisty 7.04 because their system is slow, idle CPU load is high, audio and video is choppy, might want to try the following.

Thanks to "sebdel" how posted his observation in a different thread.

Basically, ubuntu installs the 2.6.20-15-generic kernel, but it seems to cause problem on some system. After installing the 2.6.20-15-**386** kernel, all the performance problems vanished and now everything ok. No high CPU load while firefox is running, no choppy video anymore.

---

### Post by gp2x on 2007-05-22
agreed, except now youve lost any SMP capability (for core duo etc).

I think the speed issues with the generic kernel have something to do with gettimeofday calls, but I dont know why. I upgraded to 2.6.22-4 (via gutsy) and my desktop is now really quick.

Something is seriously wrong with edgy/feisty kernels for a lot of people.

---

### Post by kingtsy on 2007-05-22
How do you change kernel?

which kernel is better?

my feisty is slow.

thanks.

---

### Post by atze76 on 2007-05-23
@kingsty

if you just want to install the 2.6.20-15-386 kernel, which is in the feisty package repository, then you can do by using the "adept mananger" where you can select all kind of packages that you want to install. Just search for the "linux-386" packager and select it for installation. After install all the 386 kernel packages, you have to reboot. The 2.6.20-15-386 linux version should appear in your boot menu. Good luck.

---

### Post by sharperguy on 2007-05-23
wouldn't it be better to use i686 if you have the right processor?

---

### Post by atze76 on 2007-05-23
as far as I see, the i686 kernel package is mapped to the generic kernel, so probably it would not improve the situation in contrast to the generic kernel.

---

### Post by Darko Beta on 2007-05-23
Changing to i386 kernel will improve performance from a Pentium 4 2.8 Ghz?  I have problems with Firefox shooting my cpu up to 100%, even when just scrolling up and down (video and audio are fine, though).

Will this wreck my nvidia driver?  Not a huge deal, but just wondering.

---

### Post by kingtsy on 2007-05-23
My processor is a core duo and i don't like to loose it smp.

I will try to use the 2.6.22-4 first then if it doesn't improved the speed then i will try 2.6.20-15-386.

How do you install the 2.6.22-4?

Thanks,

---

### Post by Darko Beta on 2007-05-24
It worked!  I changed to the 386 kernel, and now my Firefox is much smoother.  My CPU doesn't jump up to 100% all the time any more.

BTW it *did* wreck my nvidia driver, but I got that fixed with a little bit of effort.

Thanks for the suggestion!

---

