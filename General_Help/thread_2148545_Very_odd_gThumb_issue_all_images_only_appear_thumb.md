---
title: "Very odd gThumb issue: all images only appear thumbnail size??"
date: 2013-05-25
forum: General Help
---

### Post by jonnymopar on 2013-05-25
Hi all.  Ubuntu 12.04 32-bit, Cinnamon 1.8.6.

I installed the latest version of gThumb the other day after reading many recommendations.  It's for Gnome, so I figured it would work well with Cinnamon, but I'm having an odd issue with it.  If I click on any image, it appears, but only the same size as the thumbnail.  Even if I go to full screen, it shows a single thumbnail in the center of the screen.  Something is goofy where it won't fit to window size.  Removing it and reinstalling it didn't make any difference.

Any recommendations on things to try?  I will say this (and this didn't dawn on me until as I was typing this post): early on, I got tired of the Nemo/Nautilus battle that takes place when you manually install Cinnamon over Ubuntu.  I removed Nautilus and haven't had any problems that I've noticed.  I both installed and reinstalled gThumb long after I did this.  I'm probably over-thinking this, but if, in removing Nautilus, I removed some random dependency required by gThumb, the installation would replace it, right?

---

### Post by Dennis N on 2013-05-25
You are correct - gthumb would not install without it's dependencies installed too.

As to your problem, It's because the needed extensions are **not** enabled.  

[B]Edit > Preferences > Extensions Tab
[/B]
Looking at mine, all the extensions are checked, **except for**:

23
Audio Visual Support
Bookmarks
Facebook
Flicker
Photo Bucket
Picasa Web Albums
Raw format support
Red eye removal
Web albums

---

### Post by jonnymopar on 2013-05-26
I set up my extensions exactly how you have yours, and it seems to be working fine now!  Thanks for the quick help!

Once I set all the extensions, it came up with a dialog saying "a restart is required".  Not knowing that it meant the program, not the computer, I showed my true Windows user colors by closing all other programs in preparation for a system restart.  Sheesh.

---

### Post by Dennis N on 2013-05-26
In this case, closing and relaunching the program is probably enough. In other situations, it could mean reboot the computer. Glad to hear gthumb is working right now. It is a nice program.

---

