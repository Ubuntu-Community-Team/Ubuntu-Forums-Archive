---
title: "My Feisty problems"
date: 2007-04-29
forum: General Help
---

### Post by Gannin on 2007-04-29
So I did a clean install of Feisty.  It does seem a bit faster in a few areas, which is nice.  But it has some annoying problems which are making me think about going back to Edgy.

First, the mouse is much slower.  Even though I have my mouse set up the exact same way as I had it set in Dapper and Edgy, the mouse is slower and less responsive.

Second, there's something strange going on with the fonts in Firefox, regardless of which version of Firefox I use.  When a web page uses a font that comes bundled with Feisty, it renders just fine.  But when a web page uses a Microsoft TrueType font (after having installed the msttcorefonts package both automatically and manually), it renders much, much smaller than it should... even when the minimum font size is set to an appropriate level.  Even when it's set to the same level I had it set at in Dapper and Edgy, where it worked just fine.

And finally, installing the nVidia driver has turned out to be a pain.  Sure it's really easy if you want to use the nVidia driver that Ubuntu provides, but I want to use the latest driver (as I've always done before).  Even after removing the Ubuntu-provided nVidia driver and the various restricted modules packages, and after compiling and installing the nVidia driver succesfully, and after modifying xorg.conf appropriately, it still won't work, whether I manually modprobe the nvidia kernel module or not.

So, I must say, all of these wonderful things that are keeping me from being able to work the way I want to work, and are keeping me from working comfortably (especially the mouse and fonts thing) are seriously making me think about going back to Edgy.

---

### Post by dcstar on 2007-04-30
> **Gannin said:**
> 
........
Second, there's something strange going on with the fonts in Firefox, regardless of which version of Firefox I use.  When a web page uses a font that comes bundled with Feisty, it renders just fine.  But when a web page uses a Microsoft TrueType font (after having installed the msttcorefonts package both automatically and manually), it renders much, much smaller than it should... even when the minimum font size is set to an appropriate level.  Even when it's set to the same level I had it set at in Dapper and Edgy, where it worked just fine.
.......

Try this:

[http://ubuntuforums.org/showthread.php?t=343670](http://ubuntuforums.org/showthread.php?t=343670)

---

### Post by Gannin on 2007-04-30
I actually did try that, even though it looked like it was mainly geared toward LCD monitors and I use a CRT.  When I tried that, my various system fonts got really big, but the font problem in Firefox persisted... there wasn't any difference.  So I downgraded back to the original Feisty packages so my system fonts would be normal-sized again, considering it doesn't effect the Firefox font problem one way or the other.

---

### Post by Nythain on 2007-04-30
feisty uses the latest nvidia driver that i know of, the 755whatever one...its called nvidia-glx-new... they kept the 9631 as nvidia-glx because the newest driver abandoned support for popular but somewhat old cards, so now ubuntu gives you the option of keeping the last newest driver wich works great for most cards, or if you have a really new card, using the newest newest driver... i personally think that was a GREAT move on ubuntu's part because i would have hated to have lost 3d support for my card due to the driver upgrade when 3d works great with the 9631 driver

---

### Post by Gannin on 2007-04-30
I was able to take care of the nVidia issue once I discovered that the "nvidia" module had been blacklisted in /etc/modprobe.d/blacklist-restricted.  Once I removed it from the blacklist, I was able to get the nVidia driver up and running fine.  However the other two issues still persist.

---

### Post by Nythain on 2007-04-30
the other two i cant help with... i run kubuntu and my my mouse flies along like it always has... its even all glowy and transparent (i love linux, i can make EVERYTHING transparent) and i havent notice a problem YET with fonts in firefox, then again i dont visit to many sites any more these days

---

### Post by Gannin on 2007-04-30
But you do visit here, and this site actually gives me more font problems than other sites do these days.  Perhaps I'll give Kubuntu Feisty a try, just to see how it goes.

---

### Post by Nythain on 2007-04-30
yeah, i visit here... fonts are fine to me... i've never really had to jack with installing fonts or whatnot, everything has just kinda worked... most trouble i've ever had so far was configuring samba... nvidia drivers installed easily for me with feisty, my kernels actually updated for me in feisty, webpages look great for me in 3 different browsers (konqueror, firefox, and opera)... music and video playback have never given me trouble (well except dvd playback with anything other than xine-ui... everything else has horrible tearing towards top of video during light changes and fast pan and scan scenes... still tryin to figure that one out)... i havent messed with wireless yet, im still hardwired to the router.

i will point out that like others have said, kde does start to get a big sluggish after running for about a week or two straight... but i figure thats just the good lords way of saying, "back away from the computer son" :)

---

### Post by Gannin on 2007-04-30
I'm still checking out KDE.  So far it looks pretty good.  I haven't used it since I was using Mandriva as my distro (before Dapper).

As for your video tearing problem, have you tried enabling vsync?

---

### Post by MCMcButtah on 2007-04-30
I had to re-install the nvidia driver after my edgy -> fiesty upgrade. If your video driver is loading fine it probably vsync needing to be set as Gannin pointed out

---

