---
title: "virtual console has weird scanlines"
date: 2008-03-21
forum: General Help
---

### Post by t0ksik on 2008-03-21
I am having a weird problem with being unable to see the virtual console when I hit Control-Alt-F1 (at least I think that is called the virtual console).

Instead of a nice black screen with white text in which I can type, I get a weird scanline pattern.  Vertically, there are a sparse colored lines such as purple, red, blue and green and horizontally I have some weird white and gray pattern that seems to be scrolling up at an extremely fast rate.

My guess is that my refresh rate is too fast for the console part of my setup because when I turn the computer off, instead of giving me the lines to the effect of "stopping server blah blah blah blah [OK]" I get the same weird line pattern.  I am on a dell laptop (inspiron 1501 jfyi) so my screen does have a limited resolution rate.

My card was configured by Envy and this is the latest version of Gutsy (Kubuntu distro).  The xserver works perfectly, and for about 99% of the time, that is all I need, I just want this fixed for no better reason than it is broken.  (BTW, I tried out Heron alpha 6 the other day - also kubuntu - and I had the same problem with a fresh install using EnvyNG.  Well, I say fresh install but I have my /home/ folder on a seperate partition so I can just arbitrarily install distros and always have my settings work for my most commonly used programs no matter which beta I am using)

---

### Post by t0ksik on 2008-03-21
Fixed it, sorta.  Using this table:

```

Color depth      | 640x480  800x600  1024x768 1280x1024
-----------------+-------------------------------------
256        (8bit)|  769      771       773      775
32000     (15bit)|  784      787       790      793
65000     (16bit)|  785      788       791      794
16.7 Mill.(24bit)|  786      789       792      7

```

I edited /boot/grub/menu.lst and added vga=791 to the line that starts ```
# defoptions=
``` Now my Virtual Consoles work but my splash screen is gone.  I like the tradeoff, you may not.  Also, someone probably knows how to get it back.

---

