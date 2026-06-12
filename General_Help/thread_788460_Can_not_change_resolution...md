---
title: "Can not change resolution.."
date: 2008-05-09
forum: General Help
---

### Post by Worst_Enemy on 2008-05-09
Hey everybody,

I'm new to Linux and these forums so HI :)

Well my friend give me an install CD for Linux today, so I decided to try Ubuntu out, I installed it and then updated to a newest distro via the 'update manager'. 

In the old version my resolution was (I think around) 1024x768 but now I only have the option to change it to 320x240 or 640x480 the only refresh rate available is 50Hz.

I am using a Nvidia 7800 GS OC AGP Card, which on the monitor resolution settings appears as a 'cloned display'. I have also installed the hardware drivers for my card.

Is there anything I can try out to be bale to change my resolution to a higher one? As some windows dont even appear on the screen they get cut off!!

Thanks!

---

### Post by Worst_Enemy on 2008-05-09
The web browsing is also very slow, my N95 via WLAN is ten times faster than using Ubuntu and firefox! Is this normal?

---

### Post by karlatsaic on 2008-05-09
I am assuming you have your "restricted driver" enabled? 
Pull down: System/Administration/Hardware Drivers and hopefully you see your nvidia driver checked as enabled. If not, enable it and reboot. If it is, don't despair, it happened to me, too. What I did was just grabbed an old xorg.conf from the /etc/X11 directory - if you go there, and do an 'ls -ltr' you will see all these configuration files that get backed up for safety. Just take the current xorg.conf and copy it to something like xorg.conf.myfailsaife and then copy the last one (by date) before your upgrade into xorg.conf. [edit: you must sudo to copy (cp) files around in the /etc/X11 directory]. Just restart and see if it works. Hopefully that helps. There are other things you can do, including installing EnvyNG, but that might be a big install, and if the minimal suggestions above work, don't bother.
good luck...

---

### Post by Darkade on 2008-05-09
In grub (The boot manager) select the recovery mode, probably the 2nd option on the list. After a while it will ask what do you want to do:
a)resume normaly b)Start a root shell c)fix x11
Select this last option, I had a similar problem and that fixed it. hope it helps:lolflag:

---

### Post by Worst_Enemy on 2008-05-09
Thanks for the replies, I will have a try at your suggestions tomorrow! Hopefully I can get my resolution back to something decent.

Oh and yes, restricted driver is enabled!

---

### Post by karlatsaic on 2008-05-09
Also - when I upgraded, I had my restricted driver enabled. After the upgrade, it was so slow, it took > 60 seconds just to pull down the Restricted drivers menu to disable it. After I disabled it (and rebooted), it came up in a low-res, very generic mode. I then re-enabled the restricted driver and it all came back up just fine. I disabled it for another reason (no need to know why), and after that was when I had to resort to an earlier version of xorg.conf.

---

