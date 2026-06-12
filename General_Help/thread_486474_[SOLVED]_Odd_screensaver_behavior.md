---
title: "[SOLVED] Odd screensaver behavior"
date: 2007-06-28
forum: General Help
---

### Post by MadMac on 2007-06-28
I have some odd behavior gong on.  I use one of the screensavers (atunnel) that comes with Ubuntu and it is set for 47 minutes to kick on.  When I reboot the computer (or even just Ubuntu) it seems like it turns itself off and the video card seems to have some sort of “sleep" mode where it turns off the video card and the monitor also seems to “go to sleep”instead of turning on the screensaver.  It seems to have a time to go to “sleep” of about 10-15 minutes.  I can go into the screensaver and set it at the lowest time possible, then close it, then open it back up and reset it to 47 minutes and the video will then go to the screensaver and not to the "sleep” bit.  It does the same thing, no matter which one of the Ubuntu screensavers I use or what time frame.  No matter how I set it up it still does the same thing.  I hope this makes sense, it's really hard to describe in typewritten words.

I'm running 7.04, Nvidia Geforce 5500 video card with the "restricted drivers" installed.  Checking with glxgears shows some wonderful speeds (about 1345.000 average).

Any idea on why this is happening?

Thanks!

---

### Post by Keen101 on 2007-06-28
ok, so I am pretty much a noob myself, but i will try and help. From what it sounds like, you need to adjust your Power Management settings, and not your screensaver settings. However, if that is not the case, then I really don't know. But, if you think it is the screeensaver, then try unistalling gnome screensaver and give xscreensaver a try. (which I like better)


Good luck
-Keen101

---

### Post by MadMac on 2007-06-28
> **Keen101 said:**
> ok, so I am pretty much a noob myself, but i will try and help. From what it sounds like, you need to adjust your Power Management settings, and not your screensaver settings. However, if that is not the case, then I really don't know. But, if you think it is the screeensaver, then try unistalling gnome screensaver and give xscreensaver a try. (which I like better)


Sorry, I forgot to mention that I also set and then reset the power management, just like the screensaver - down to practically nothing (7 minutes, I believe), close, re-open, then back up to "never".

I'll take a looksee at that program, though.

Thanks!

---

### Post by MadMac on 2007-07-01
> **ok, so I am pretty much a noob myself, but i will try and help. From what it sounds like, you need to adjust your Power Management settings, and not your screensaver settings. However, if that is not the case, then I really don't know. But, if you think it is the screeensaver, then try unistalling gnome screensaver and give xscreensaver a try. (which I like better)

MadMac said:**
> Sorry, I forgot to mention that I also set and then reset the power management, just like the screensaver - down to practically nothing (7 minutes, I believe), close, re-open, then back up to "never".

I'll take a looksee at that program, though.

Thanks!

Sorry, but no joy.  I took a look at that program, but it's just not for me.  Thanks anyway!

---

### Post by MadMac on 2007-08-26
[Late post]

Got it.  Most likely was that I had a bad hard drive.  No problems now!

Thanks to all that helped!

---

