---
title: "Top left of screen issues:"
date: 2019-09-13
forum: General Help
---

### Post by kesetyan on 2019-09-13
Hi,

This is probably something fairly basic and simple to change and something I should be aware of but, as yet, I've not found the solution.  When my mouse pointer goes to the top left of the screen, the desktop disappears.  I can get it back easily but I find this behaviour a bit irritating at times particularly as program's 'File' dropdown menu is located in that area when the window is maximized.  It is easy to slightly overshoot with the mouse pointer and then the desktop temporarily disappears with its contents.

Is there a simple way I can adjust this behaviour?

Thanks.

---

### Post by TheFu on 2019-09-14
Just a guess, probably wrong, but moving the mouse off screen is how to switch to a different desktop workspace.  These are virtual desktops for which you control the location by saying you want a 3x3 or 2x2 or 1x4 or 3x1 workspace setup. I suppose a 9x9 could be setup.  [https://en.wikipedia.org/wiki/Virtual_desktop](https://en.wikipedia.org/wiki/Virtual_desktop)  I've been using a virtual desktop since the mid-1990s to help organize my workspaces by task.

Whenever asking GUI questions, please always say the Ubuntu release number and the GUI being used.  There are about 20 different GUIs, so please don't make us guess. GUI answers are different based on the DE (Desktop environment) and WM (Window Manager) used and the specific release.

---

### Post by Dennis N on 2019-09-14
> Is there a simple way I can adjust this behaviour?
It's called a 'hot corner'. You can turn it off and on in Ubuntu 18.04 from Tweaks > Top Bar > Activities Overview Hot Corner > Off/On.

---

### Post by kesetyan on 2019-09-15
Hi Fu and Dennis,

Thanks for your quick replies.

The issue was the 'Hot Corner'.  'Activities Overview Hot Corner' was switched off in 'Tweaks' yet was still functioning for some reason.  However by turning it back on, testing it afew times and then turning it off again, the issue now has been resolved.  Thank you for pointing me in the right direction Dennis and ultimately solving my problem.

---

### Post by kesetyan on 2019-09-15
Hi again,

I spoke too soon.  Disabling the 'Hot Corner' via 'Tweaks' proved only a temporary solution as when I restarted the computer, the active hotspot reappeared despite 'Tweaks' showing it as 'OFF'.  However, after much searching of the internet I think I've found a resolution. I downloaded and installed a Gnome shell extension ('No topleft hot corner') and that has successfully survived my system restarts today.

---

