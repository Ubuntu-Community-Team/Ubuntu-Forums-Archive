---
title: "[Hardy Heron] Customization issues"
date: 2008-04-25
forum: General Help
---

### Post by Taling Hallenthur on 2008-04-25
Hello there! I installed Hardy yesterday and I encountered two problems so far:
- wallpaper scaling sucks. I tried to setup a wallpaper that has bigger res than my screen and when I choose the center option in the appearance window, the wall is shifted to the left.
- there is something wrong about compiz. I let the drivers manager download all the stuff needed and I run compiz. It seems to run slower than the one bundled with Gutsy and after a reboot I just got a quarter of the screen visible, the rest was black. 
Both of these issues didn't exist on my Gutsy Gibbon install. Do you have any ideas what to do about these problems??

---

### Post by james.wong on 2008-04-27
On your second point, I seem to remember that I may have had that problem before - just a small section of the screen is visible in the top-left corner of the screen.

It may be possible to fix this by going into the CompizConfig Settings Manager, selecting "General Options" and editing the settings within the "Display Settings" tab. Look inside where it says "Outputs".

Now I'm not entirely sure on this but the value in here may be the area of the screen to display. If it says something like "640x480+0+0", try changing it to the screen resolution you usually use.

---

