---
title: "Ubuntu changes keyboard layout on its own"
date: 2023-09-15
forum: General Help
---

### Post by smart-mart on 2023-09-15
Hi All,

I've been experiencing a strange bug for a few months now.
I haven't figured out the circumstances of when this happens, My keyboard layout would switch from English to American.
I don't have the american keyboard layout as an option on my system,

to fix it I need to add an extra keyboard layout to display the en1 in the top right
and click on English (UK) which is the currently selected.

This seems to make Ubuntu realise its supposed to be using English, then I can go back into settings an remove the unnecessary keyboard layout,

Is there any way to prevent this behaviour?


I am using Ubuntu 23.04

---

### Post by TheFu on 2023-09-15
Do you mean UK?  Keyboards are tied to the locale first, language second.  There are different keyboards for AUS, CA, US, and UK English.

Typically, there are 2 places where keyboards are set.  For the console and for the display server (X11 or Wayland).  

To change the console keyboard, 
```
sudo dpkg-reconfigure keyboard-configuration
```

For the display server, there are far too many ways to get there.  The DE probably has a way to change it and that's the easiest way.  Check the **user guide** for the DE for how.  For Gnome, [https://help.ubuntu.com/stable/ubuntu-help/keyboard.html.en](https://help.ubuntu.com/stable/ubuntu-help/keyboard.html.en)
XFCE, Mate, KDE, LXQt, et al, will each be different.

---

