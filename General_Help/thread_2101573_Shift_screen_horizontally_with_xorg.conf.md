---
title: "Shift screen horizontally with xorg.conf?"
date: 2013-01-05
forum: General Help
---

### Post by vancinas on 2013-01-05
I just hooked a cheap 1280x720 HDMI monitor up to my laptop and everything's fine except for one thing: the picture is shifted off the left edge of the monitor by maybe 100 pixels. The monitor's built-in menu has an option to shift the image horizontally, but, being cheap, it only allows you to shift it so far, and that's not enough to bring the whole image on to the screen.

I was wondering if it would be possible to use the xorg.conf file to specify an offset position for the image on the monitor. Does anybody know if that can be done? Thanks!

---

### Post by Wim Sturkenboom on 2013-01-05
Yep, it should be possible. I don't have the time to research it but I've done it long ago (with Ubuntu 6.06 or 8.04) where adjusting the monitor itself was not an option as Windows used slightly different setting compared to X.

Step 1 would be to generate an xorg file; a search for 'generate xorg' on the web should get you started; one hit that I found is [http://www.cyberciti.biz/tips/create-a-xorgconf-file.html](http://www.cyberciti.biz/tips/create-a-xorgconf-file.html) but I did not test it.

Step 2 would be to create a modeline using e.g cvt
```

wim@aa0:~$ **[COLOR="Red"]cvt 1280 720 60[/COLOR]**
# 1280x720 59.86 Hz (CVT 0.92M9) hsync: 44.77 kHz; pclk: 74.50 MHz
Modeline "1280x720_60.00"   74.50  1280 _1344 1472 1664_  720 723 728 748 -hsync +vsync
wim@aa0:~$

```

The following needs to be researched as I can't remember.
a)
Add the modeline tothe appropriate section of the xorg.conf
b)
Add a reference in another section in xorg.conf to use that modeline
c)
Restart X (or the system)
d)
Play with the underlined numbers (do your research; e.g. [http://arachnoid.com/modelines/index.html](http://arachnoid.com/modelines/index.html)) and go back to c); repeat till your happy

---

### Post by vancinas on 2013-01-09
Okay, so while I'm trying to figure out how to get xorg.conf to work, I'm also trying to use xvidtune. The problem is that when I start xvidtune, it defaults to adjusting the settings for my main monitor, which doesn't need adjustment. In this case it always gives an "invalid mode requested" error for any change I make, no matter what. What I want to do is get it to adjust the settings for my secondary monitor. Is there any way to specify which monitor xvidtune adjusts?

Still haven't made much headway with the xorg.conf. I can't manage to generate one on my system (I always get an error that says, "Number of created screens does not match number of detected devices. Configuration failed."). After the error there is a file called xorg.conf.new in my home directory, but it appears set to empty defaults (and it has 4 monitor sections even though I really only have two monitors). Anyone know how I can get around the error when I try to generate the .conf file?

---

### Post by vancinas on 2013-01-10
bump

---

