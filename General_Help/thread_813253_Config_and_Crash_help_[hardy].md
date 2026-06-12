---
title: "Config and Crash help [hardy]"
date: 2008-05-30
forum: General Help
---

### Post by RyanFlemington on 2008-05-30
Hey there, first time posting here(recent windoze-convert). Been solving my own problems up until now, but I'm kinda stumped. 
    Anyway, I'm tring to change my xorg.conf so that I can use the back/forward buttons on my MX510 mouse. I've tried just about every walk through and configurationg I can find, and nothing. Eveytime I Ctrl-Shift-Backspace to restart x, I end up staring at a blank cursor(this happens everytime, whether I've changed xorg.conf or not). I can space down, but can't type. I can still access virtual terminals. 
   If I reboot instead, KDM seems to stop running at "running local boot scripts     (/etc/rc.local)    [ok]"
This happened before, when I was trying to get nvidia drivers work. I have to reload a backed-up xorg and it runs fine. Any help here is grealy appreciated.

Here are my specs, incase it's relevant:
-Q6600 b3 stepping
-Gigabyte GA p35 DS3R rev 2.0
-2GB Corsair xms2 600
-nVidia 8800 GTS oc-version
-some crappy samsung hd I use for experimenting

[post scripts:]
// if you have some spare time on your hands, and feel like solving some more of my problems, issues, and annoyances, here they are:
-clicking in a URL bar doesn't auto-highlight whatever's there.
-haven't figured out how to auto-start amsn yet.
-no task bar on my left monitor, the right being the main(also, they are different native resolutions, and the left monitor has extra desktop below the bottom of the monitor. I would also like to be able to adjust gamma for each independant monitor.
-audio isn't working
kthxbai ^.^ lol

---

### Post by RyanFlemington on 2008-05-30
bump- anyone?

---

### Post by prshah on 2008-05-31
> **RyanFlemington said:**
> 
   If I reboot instead, KDM seems to stop running at "running local boot scripts     (/etc/rc.local)    [ok]"

The last line in your /etc/rc.local should be "exit 0", followed by a blank line. Can you confirm this is your case?

---

