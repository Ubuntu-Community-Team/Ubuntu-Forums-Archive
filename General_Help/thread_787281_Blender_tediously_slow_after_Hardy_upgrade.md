---
title: "Blender tediously slow after Hardy upgrade"
date: 2008-05-08
forum: General Help
---

### Post by drewcoon on 2008-05-08
Hey, I'm into 3D rendering, so I'm really getting frustrated that Blender 3D doesn't run properly after I upgraded from Gutsy.

While running the file manager in Blender (while opening or saving a file, for example), everything slows to a crawl. Simply putting the mouse pointer over the "Open" button for it to light up causes the processor to max 100% for a few seconds before the button finally lights up with a rollover animation.

I'm completely stumped on how to fix this. There is no output when Blender is run in terminal, and I definitely never had this problem with my Gutsy install.

Can anyone help? I really would like Blender to work again :)

(I'm currently apt-removing blender and getting it off the blender3d.org site.. I'll tell you how it goes)

---

### Post by skymera on 2008-05-08
Don't suppose your running do you?

If so turn it off and you should get a major speed boost.

---

### Post by drewcoon on 2008-05-08
> **skymera said:**
> Don't suppose your running do you?

If so turn it off and you should get a major speed boost.

Sorry I don't understand you... Running what? You might have left a word out :p

If you are talking about compiz, it's already off. My comp can't really handle it to begin with.

I just tried removing blender and reinstalling but no success. Is there a way to get the older versions of Blender? I'm wanting to try the version that I had pre-upgrade, and see if that could be the cause of the problem.

---

### Post by skymera on 2008-05-08
O so i did! silly me, TV distracting.

Yeah i mean compiz.

What is your video card?

---

### Post by drewcoon on 2008-05-08
> **skymera said:**
> O so i did! silly me, TV distracting.

Yeah i mean compiz.

What is your video card?

It's an ATI Radeon Xpress 200 (it's onboard).

I know it's a crappy setup (onboard + ATI + Linux = bad things), but it worked fine with Blender before.

This leads me to think that there could be some bugs with my ATI driver being compatible with the newest Blender release. I'm looking into trying an older version, if I can find one.

Thanks for the help by the way, I appreciate it :)

---

### Post by skymera on 2008-05-08
Yeah drivers, hmm.

Maybe try to reinstall drivers uding Envy?

I've noticed higher sucess rates using it

---

### Post by drewcoon on 2008-05-08
From experience, playing with my driver usually results in me having to hack around in safe mode terminal when I blow Xorg up :p

I might try it though, because I've also noticed that my Catalyst control center no longer works prior to upgrading to Hardy, a new install might be what is needed.

I've never tried Envy before, I hope it works!

---

### Post by drewcoon on 2008-05-08
Alright, I Envy'ed my ATI driver. Didn't fix my Blender problem, but Catalyst control center is now working, which is great.

I might just leave this issue, unless someone else comes up with any ideas. I'm probably just going to go out and grab an nVidia card sometime and hope it solves my problems.

Thanks for the help :)

---

### Post by ezuli on 2008-07-23
I had same problem with my laptop. I tried regular fglrx, evny fglrx and the newest from AMD. I also tried 0.46 Blender, but every combination was way too slow even with pop-up menus.

I noticed that Blender was actually more usable with faulty fglrx-setup (no dri, MESA indirect). So I removed fglrx totally and changed driver in xorg.conf to "ati". Now Blender runs smoothly with no glithces.

---

