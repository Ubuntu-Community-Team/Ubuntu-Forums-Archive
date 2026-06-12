---
title: "DVD player, xV problems"
date: 2005-08-26
forum: General Help
---

### Post by gradedcheese on 2005-08-26
Hello.  I still cannot get my DVDs to play reasonably :(  I'm hoping someone can point me in the right direction.

This is on an IBM ThinkPad T22.  I can get sound when I play DVDs but I cannot get video, I get a blue screen instead.  libdvdcss2 is installed.  In Multimedia Systems Selector, the sink that has xV does not work.  The 'no xV' one does work for the demo.  Similarly, when I first installed and ran xine, it did it's xine check and found that 'xV doesn't work' ...I can only play DVDs in one case: if I am using xine, switched to 'xshm' as the video driver.  In that case the movie plays but the performance is horrible (and DMA is on for my drive).

The crazy thing is that this used to work... when I first installed Hoary and installed libdvdcss2, I was able to play a DVD in totem-xine just fine!  I even tried, using a spare hard disk, installing Ubuntu from scratch, not running any updates, and installing xine and libdvdcss2... strangely enough, I had the same problem.  I then tried, for the heck of it, Warty on the spare hard disk (same problem).

What are my options for troubleshooting the xV thing?  I don't know much about xV/libxv/etc  but perhaps something is not configured correctly somewhere (xorg?)

 ](*,)  as I am typing this, I just realized that, when this all worked, the only difference was that I was using my laptop on its own with its built-in screen.  During my frustrating attempts of late I have been using an external LCD monitor with it through a docking station.  Perhaps that has something to do with it.  I'll try that now but I'll appreciate any other ideas.  Thanks!

---

### Post by gradedcheese on 2005-08-26
Well, it look like more of a 'thinkpad' problem than an Ubuntu problem!

Everything works fine (xV in the sink test and actually playing DVDs) as long as I didn't boot up the laptop in 'docking' mode!  The way it does not work is:

1) place the laptop, with the lid closed, in the docking station
2) press the power button on the docking station
3) laptop boots up using the external monitor

The way it does work is to just have the laptop booted up on its internal monitor and then switch to the extrnal one via the theyboard shortcut (Fn+F7 in my case).

Why this makes a difference for xV is really beyond me.  I suspect that's more of a question for the linux thinkpad group but perhaps someone here will find this whole mess interesting.

---

