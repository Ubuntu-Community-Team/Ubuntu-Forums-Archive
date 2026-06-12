---
title: "Unity Tweak Tool doesn't change fonts and themes settings in 14.04.01"
date: 2014-11-07
forum: General Help
---

### Post by david310 on 2014-11-07
Using Ubuntu 14.04.01 in a VirtualBox machine, Unity Tweak Tool works perfectly, it changes everything, including font (antialiasing, hinting etc.) and themes settings.

However, after installin Ubuntu in a spare drive (not a virtual machine), Unity Tweak Tool doesn't seem to work properly. Even if I select different hinting options, fonts are still the same. It also doesn't change themes.

What's happening? Is it because I'm using an LCD TV connected to the HDMI output of the video card? Or maybe NVIDIA drivers?

---

### Post by Carl_Witthoft on 2014-11-26
I am experiencing the same problem.  Ubuntu14.04.01;  after installing, the  Appearance tab in System Settings sees only three themes, even tho' there are 8 or 9 in /usr/share/themes.  I have tried using  Unity Tweak Tool, which at least shows all the existing themes in its list, but clicking on them does not switch the theme actually in use.

I'm guessing a lock file somewhere, but have no idea where to look.

EDIT:  I grabbed some hints over at [http://ubuntuforums.org/showthread.php?t=2230562](http://ubuntuforums.org/showthread.php?t=2230562)   and had success selecting themes via gnome-tweak-tool.

---

