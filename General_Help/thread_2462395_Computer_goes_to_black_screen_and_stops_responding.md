---
title: "Computer goes to black screen and stops responding after being left idle for a bit"
date: 2021-05-19
forum: General Help
---

### Post by TuxGirl on 2021-05-19
I have a desktop machine that I have been experimenting with Ubuntu on. I tried Ubuntu mate 21.04, and ran into this issue along with others. Also tried 20.10, and now using xubuntu 20.04. For both 21.04 and 20.10, I was told the issue could be due to bugs in Ubuntu, but as the LTS version, I would expect 20.04 to be stable and not have this issue! 

So, any time I leave the computer idle for very long, I come back and it has a black screen and is completely unresponsive. The only way to get it back is to force shutdown with the power button. 

This happened also on the Ubuntu livecd, and during installation, btw. 

I have changed the power management settings to tell it never to suspend or hibernate. In the bios, it's set to not attempt to suspend to ram. I also updated /etc/default/acpi-support and set SUSPEND_METHODS="none", then restarted acpid. 

It looks like the power management settings reset to having a screen timeout, so I just turned that off again, but even with that turned off, the screen still seems to blank and pop me out to the switch user screen if I don't touch anything for 5 minutes, so that doesn't seem to work right. 

I'm honestly befuddled as to what is going on. I ran journalctl, and i don't see anything suspicious before the -- Reboot --. 

Important detail: this machine does have an Nvidia graphics card. I haven't yet set it up, so it's currently using nouveau. I know that Nvidia is hit and miss sometimes in Linux, but this machine didn't have this particular issue when it was running manjaro a while back. I'm considering trying a couple liveusbs to see if there are some distros that don't have this issue at all. 

Any advice on how to debug this or how to prevent this issue from recurring?

---

### Post by rbmorse on 2021-05-19
Is this desktop machine perhaps built around an AMD x570 or B550 chipset with a 3xxx series AMD CPU?  There is a known hardware issue for those machines when left for indeterminate periods at low power/idle.   There's a work around for that.

---

### Post by dragonfly41 on 2021-05-19
I can only think of a temporary fix .. perhaps just have a cronjob which (after some time?) emulates some 
key or mouse actions to convince the system not to suspend.

xdotool (for one) can emulate key and mouse actions through bash script.

Of course you still need to figure out why.

---

