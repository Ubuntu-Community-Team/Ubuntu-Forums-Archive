---
title: "Issue with Grub or Plymouth"
date: 2013-11-06
forum: General Help
---

### Post by mickee384 on 2013-11-06
Hi!

I accidentally blew away the grub, so recreated it. After that point, the Plymouth splash screen stopped showing. I tried to re-add it but found that hal was deprecated and therefore hwinfo. So I think that is where I screwed it up. I didn't know about the missing pkg hwinfo, and attempted to set the Plymouth resolution to 1024x768-24. When I boot, it now says that the video cannot be loaded. Then blank screen, then a very colourful screen on thousands of vertical lines, then black, then I get the ubuntu login. all works from there. I see Plymouth on shutdown, but when I tried 'fixing' Plymouth I see I don't have, can't have hwifo. Is there another way to make the video available for boot up? I have a Nvidia 9300GS card. Much thanks!

---

### Post by mickee384 on 2013-11-07
Got a bit father. I now have the Plymouth screen, starts with "Ubuntu 13.10" in a weird small font, then that moves to about the 10 o'clock position on the screen. the tiny dots move then I see "Failed to claim resource 0". Is resource 0 the one assigned to Plymouth? Is there some code that I should try to get and post that here? Plymouth works great on shutdown. Ended up downloading a program, Boot Repair, and recreated the grub, purging the old one. Then I ran a script called fixplymouth ([http://www.webupd8.org/2010/10/script-to-fix-ubuntu-plymouth-for.html](http://www.webupd8.org/2010/10/script-to-fix-ubuntu-plymouth-for.html)) , set resolution to 1024x768-24, (even though none were listed because there is no hwinfo), rebooted and its fixed. Solved

---

