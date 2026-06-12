---
title: "Weird resolution Problem"
date: 2007-12-19
forum: General Help
---

### Post by dethredic on 2007-12-19
Ok, my normal screen resolution is 1280x1024. Sometimes when I restart my computer my resolution is changed to 1600x1200. This is a wide screen resolution, but it seems to fit on my square screen. I change it back to 1280x1024, and it says, do you want to keep this resolution and I click "Yes", but the resolution doesn't change. When I restart again, then resolution is back to normal. If I don't change the resolution and restart the resolution is still 1600x1200 and the edges of my screen are cut off, like I would have expected from a wide screen resolution.

It has happened a couple times randomly, but It usually happens when I change Compiz setting I think.I can't say it only happens then, or it always happens then, but I think there might be a connection.

Has anyone else had this problem?

---

### Post by allegro63 on 2007-12-19
i too am having resolution issues.

My resolution is way too low, making impossible to do some functions, like seeing an entire window for things.

When I try to change the resolution to make things smaller, I don't have a choice of sizes, I have the one, ONLY. I have no idea how to resolve this issue.

I am new to this OS, it looks like it will be great once I get past the learning curve, and issue like this one...the only other main issue is an inability to save bookmarks on my browser(firefox naturally).

any help along these issues would be welcome.

---

### Post by dethredic on 2007-12-20
ok, it just happened to me again.

---

### Post by Rick Myers on 2007-12-20
I've had a couple machines that didn't like the standard resolution provided by X. The problems I experienced were slightly different but the resolution I used may work.

Make a backup copy of /etc/X11/xorg.conf. Then modify xorg.conf under the section "screen", sub section "Display". Remove the resolution value 1600x1200 (and any value that precedes) leaving something like: "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480". Then restart X. If you're not sure how to restart X just reboot the machine. 

BE WARNED: Screwing with xorg.conf can render your machine incapable of booting to the GUI. Make sure you are able to modify xorg.conf from the command line before you proceed.

---

### Post by Jerry N on 2007-12-20
The same thing happened to me this morning.  I reset the resolution to 1280 x 1024 successfully and then rebooted - right back to 1280 x 1024.  I assume this has something to do with some recent update.  I have all screen effects, including the Compiz thing, shut off.  Also 50 hz is the only screen refresh rate available although my Samsung monitor reports that it is operating at 60. 

Jerry

---

### Post by oscarsfriend on 2007-12-20
It is worth mentioning this here in case anyone comes searching for it.  About a month or so ago my monitor started occasionally using 1024x768 on start-up instead of 1280x1024.  Restarting X would fix it.  This suddenly started out of the blue, and I had no idea what was going on.  Looking though the logs I realized what was happening.  I had started switching my monitor off at the plug rather than just on the front of the monitor itself.  I would occasionally forget to switch it on at the plug until after my machine had started up, and X wouldn't see my monitor to get the settings (the monitor will report the settings when switched off on the front of the monitor, which is really just a standby mode).  The fix was to modify the monitor section of xorg.conf for my specific monitor (frequencies etc), which are generic by default, so X will detect your monitor.  (This is all on Feisty, BTW.)

---

### Post by dethredic on 2007-12-20
Ok, well I am getting a new monitor for christmas, so I will see if that fixes things.

---

