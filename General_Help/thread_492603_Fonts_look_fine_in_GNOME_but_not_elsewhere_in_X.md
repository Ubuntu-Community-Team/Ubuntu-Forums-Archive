---
title: "Fonts look fine in GNOME but not elsewhere in X"
date: 2007-07-04
forum: General Help
---

### Post by gnuvince on 2007-07-04
Hello everyone,

I bought a new PC today and I installed Feisty Fawn (7.04) on it.  I now have a weird problem with X.org and fonts.  My video card is an Nvidia GeForce 6150 (supported) and my monitor is an LCD Acer AL1916AW with a native resolution of 1440x900.

I normally use the Openbox window manager, but since I reinstalled, the fonts in X (all applications: rxvt, GTK apps, etc.) are fuzzy and jagged.  This happens only in 1440x900; when I try lower resolutions, the fonts look fine.

I tried to fix the problem by putting the correct HorizSync and VertRefresh options in the Monitor section of my xorg.conf file, by putting a ModeLine, but nothing seemed to work.  I tried the subpixel thing, but this didn't improve the quality of the fonts.

Out of desperation, I went into GNOME, and at first the fonts were blurry.  However it was possible to change the refresh rate of the monitor.  I was at 50 Hz and the only other choice was 51 Hz.  I didn't think it'd mattered, but I selected 51 Hz anyway and applied the change.  Lo and behold, my fonts were now very clear and crisp!

I am now wondering if anyone has had a similar issue and how s/he fixed it.  I don't like GNOME too much, so I'd really love it if someone had a brilliant idea on how to resolve my problem so that I could go back to Openbox.

I would post screenshots of the difference, but when I look at the screenshot of the jagged fonts in GNOME, they are clear as day.  This tells me that the problem isn't with the fonts themselves but with X.org's rendering.

Thank you for your time,

Vincent.

---

### Post by gnuvince on 2007-07-05
I don't like to bump threads, but I would really love if anyone had any idea.

Vincent

---

### Post by Surkow on 2007-07-05
When you alter your xorg configuration it should have effect on all other environments as well. I had problems with my refreshrate but I was able to solve the problem by changing the horizontal and vertical refreshrate of my monitor in xorg-conf (85hz 1280*960 CRT). LCD screens works a little different...so I can't really give advice.

---

### Post by gnuvince on 2007-07-05
Got it!  The trick was to get the correct Modeline in xorg.conf.  I found the correct line at this URL: [http://eccentric.cx/wordpress/?p=112](http://eccentric.cx/wordpress/?p=112)

Hopefully this will help someone else

---

