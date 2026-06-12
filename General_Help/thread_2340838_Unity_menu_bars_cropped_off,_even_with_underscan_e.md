---
title: "Unity menu bars cropped off, even with underscan enabled"
date: 2016-10-22
forum: General Help
---

### Post by cidthecoatrack on 2016-10-22
Hello world.  So my installation of Ubuntu has run into an interesting problem.  The computer is hooked up to a TV that does not know how to NOT perform an overscan.  So, to counter this in the past, I have used the underscan feature in my xorg settings to make it fit in the window.

However, after updating to 16.04, the Unity menus no longer respect any underscan settings.  I can't see my recycle bin or the clock in the top bar, even though all other windows adjust to the underscan and behave accordingly.  This gets particularly frustrating when watching a video full-screen - subtitles appear below the bottom of the screen, and the progress bar is missing entirely.

I have since updated to 16.10 in the hopes that it would fix this, but it has not.
[IMG]https://s21.postimg.org/9m8tcuuyt/Screenshot_from_2016_10_22_11_49_55.png[/IMG]

You can see how the menu bars on the right do end at the bottom of the sceeen - but the clock is missing from the top right, and the recycling bin is missing from the bottom left - although you can see the bare edge of each.

I do not know what to do about this, since underscan was my end-all-be-all fix for this for so long.  Any help would be greatly appreciated

---

### Post by RobGoss on 2016-10-22
Have you tried going in to the display settings and change the resolutions it looks like your settings maybe off a bit

---

### Post by efflandt on 2016-10-23
What type of video cable are you using VGA, DVI, or HDMI? VGA cannot tell what resolution your screen is. I notice that at 1080p even using digital video (DVI to HDMI cable) my screen is over scanned if I set my TV to "16:9", but is perfectly sized and centered with a setting on an LG HDTV called "Just Scan" which does its best to size whatever video signal to the screen size, even different resolutions that the TV supports. I think Samsung calls that "Fill Screen".

But I don't think that "Just Scan" is available for VGA. When I would connect an old laptop with VGA cable to the TV I had to come up with a custom modeline to adjust it to fit the screen, but using a script with xrandr commands because I did not know how to do that in xorg.conf and it was just temporary to see how it worked. The commands "cvt" or gtf" (see man pages) would come up with modeline that was close, but not necessarily perfect.

---

