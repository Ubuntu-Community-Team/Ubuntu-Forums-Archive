---
title: "GDM Crash on startup"
date: 2006-11-19
forum: General Help
---

### Post by T3h_Dohtem on 2006-11-19
Just installed 6.10. I had to do a command line install then aptitude gdm gdm-themes and ubuntu-desktop. Now on startup, when I get to the GDM login screen, my PC just locks up. If I boot up in recovery mode and do a "gdm --no-console" I can still use my XDMCP and get a login and desktop. I guess Im going to try to get it set to boot up that way, but it would be nice to get a console desktop too if anyone has any ideas.

Thanks

---

### Post by T3h_Dohtem on 2006-11-21
Well just tried a reinstall with Xubuntu and first boot was fine, then I locked up at the splash screen on shutdown, and now I'm back to freezing when GDM starts up the login screen.

---

### Post by lavaramano on 2007-01-04
i'm having exactly the same problem as t3h_Dohtem.
i've tried with dpkg-reconfigure xserver-xorg and didn't worked.
tried with dpkg-reconfigure gdm and didn't worked either.

any solution?

---

### Post by jgbiggs on 2007-01-19
I am getting same behavior, crash on gdm startup.

It bumps out to a themeless login screen with no problems from there.

Changing from the custom theme I had to Human gave the same results, a crash.

Was gdm updated recently?

./out

---

### Post by mock on 2007-02-11
I have the exact same problem.

I have had this before.

What i have done is that i updated the kernel ( and nvidiadriver of course) but yet the gdm crash to a ugly welcomescreen (themeless). From there on it works great. even gdmsetup takes a long time to work with. (could this be of any conflict with permissions when i'm now using a new kernel?)

I would really like to be able to use a theme based gdm so any help on this matter is appreciated.

are there any tricks we can try?

i will try to reinstall the nvidia driver again...
( i had the same problem before when i updated the nvidia driver, i solved it by making a clean install of ubuntu, but hope that i'm not forced to do that!)

---

