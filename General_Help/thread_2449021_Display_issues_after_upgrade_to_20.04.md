---
title: "Display issues after upgrade to 20.04"
date: 2020-08-18
forum: General Help
---

### Post by trmcdonald on 2020-08-18
I have two issues after upgrading ubuntu (Ubuntu Studio) from 18.xx to 20.04 on my laptop.

The first one is that my display is distorted. When I first log-in the background displays correctly, but as soon as I click on any of the top menu bar items the screen becomes distorted. 

[ATTACH=CONFIG]286759[/ATTACH]

If I connect an external monitor (HDMI or VGA) the display is no longer distorted.  

If I try to save the settings when I do connect the monitor, the display becomes distorted on both monitors when I click Apply.

The second issue is that I do not see an option to extend the displays - this could be due to my inexperience with ubuntu - I've used other flavours of linux in the past, but have been satisfied for the most part with Ubuntu Studio.

[ATTACH=CONFIG]286760[/ATTACH]

I have seen reports that there are issues with AMD, my laptop has an A12 AMD label on it. I did try the recommendation of using the following command: xfconf-query -c xfwm4 -p /general/vblank_mode -t string -s "glx" --create
The command did not improve the issue.

Any help would be greatly appreciated.

---

### Post by trmcdonald on 2020-08-18
> **trmcdonald said:**
> I have two issues after upgrading ubuntu (Ubuntu Studio) from 18.xx to 20.04 on my laptop.

.

The issue got worse, but after using CTRL-ALT-F2 to get to a terminal I rebooted and the issue resolved itself. 
Perhaps I needed to reboot after sending this command: xfconf-query -c xfwm4 -p /general/vblank_mode -t string -s "glx" --create

---

