---
title: "Aspect ratio 'wrong' after crash during upgrade"
date: 2016-04-28
forum: General Help
---

### Post by DrDvorak on 2016-04-28
Hello,

when prompted by the Software Updater, I decided to upgrade my Lubuntu desktop PC to the new version 16. The upgrade had reached the point of installing the packages, but during that step there was a power cut! After the power came back on I checked later and found the PC would not boot!

I did some Googling and found out about a concept of 'chroot recovery' using a Live CD. It was all very new to a dummy like me, but I was able to boot off an Ubuntu USB drive and run the commands specified such that I could eventually run the key command...

[FONT=courier new]sudo dpkg --configure -a[/FONT]

...which apparently fixes partially-installed packages.

The PC was at least then able to boot and let me log into Lubuntu, albeit *with* the new aspect ratio problems I will get to shortly. I ran the Software Updater which suggested proceeding with a Partial Upgrade. Eventually the Software Updater finished and as far as it's concerned, this is an up-to-date instance of Lubuntu 16.04.

However, the aspect ratio problem remains. Basically: the screen displays content as 'too wide' and 'squashed from top to bottom'. This is despite using the same 1024x768 resolution on the same monitor, all of which looked perfectly good on the previous version of Lubuntu.

I have attached some screen shots to illustrate the problem. In particular, see how circles are displayed as ovals!

It seemed highly likely that the problem was a knock-on effect of the power cut/crash during upgrade and/or me doing an imperfect recovery from it. I next tried running the upgrade on my Lubuntu Netbook. Free of power cuts, the upgrade completed with the aspect ratio remaining 'correct' and everything looking nice and easy to read.

Does anyone know how the aspect ratio on the desktop PC can be 'fixed'?


[ATTACH=CONFIG]268701[/ATTACH][ATTACH=CONFIG]268700[/ATTACH][ATTACH=CONFIG]268699[/ATTACH][ATTACH=CONFIG]268698[/ATTACH]

---

### Post by DrDvorak on 2016-05-01
I have got to the bottom of the problem now.
Firstly, I now believe the statement '...despite using the same 1024x768 resolution on the same monitor...' is an incorrect assumption. And that 1024x768 is just not a suitable resolution to get a decent-looking display on the monitor (actually LCD television) that I am using, because it fills the available screen space and is using a 4:3 aspect ratio, which then looks wrong on that monitor. I believe that the 'best' resolution to use 'disappeared' from the monitor preference options as a knock-on effect of the crash and attempts to repair.

It's also apparent to me that when looking at my attachments on a computer that does *not* have the problem, the pictures look fine, and the circles are circles, not ovals.

So, the way forward is make the PC aware of a suitable monitor setting, and then instruct it to use it.

The following 3-line script corrects the issue during a session:


[FONT=courier new]xrandr --newmode "1360x768_60.00"  84.72  1360 1424 1568 1776  768 769 772 795  -HSync +Vsync
xrandr --addmode DVI-0 1360x768_60.00
xrandr --output DVI-0 --mode 1360x768_60.00[/FONT]


The correction is 'lost' after reboot, so I need to rerun the script each time I do a fresh login (which is of course easy to do). I'm guessing that finding a way to 'save' these changes in the PC's settings so they persist shouldn't be very hard - I'll have a look later when I get a minute if no-one on here beats me to the solution.

---

### Post by DrDvorak on 2016-05-01
In case anyone else needs to know how to make changes permanent, one technique I found on searches that has worked for me is to add the aforementioned 3 lines to a file /usr/sbin/lightdm-session.

The page I found suggested adding the lines below the section:

[FONT=courier new]# Load profile
for file in "/etc/profile" "$HOME/.profile" "/etc/xprofile" "$HOME/.xprofile"; do
    if [ -f "$file" ]; then
        source_with_error_check "$file"
    fi
done[/FONT]


It's worked for me and been tested across 3 reboots.

---

### Post by DrDvorak on 2016-07-31
I recently 'lost' the fix, with the PC going back to using the 'wrong' aspect ratio. Evidently the (non-standard) changes I made to[FONT=courier new] /usr/sbin/lightdm-session [/FONT]were, perhaps understandably, overwritten by automatic software updates.

At least I had this solution bookmarked and have thus successfully repeated the exact same change.

At the end of the day, when my PC had the crash during upgrade with the subsequent attempted recovery, it ceased to be a 'clean build' and so it's not really surprising that the odd little workaround like this will be needed for it.

---

### Post by DrDvorak on 2016-08-16
Had to redo the fix again just now after running the Software Updater. I guess soon I will have it learned by heart, even if I don't really understand it properly.

---

