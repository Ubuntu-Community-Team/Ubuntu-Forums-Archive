---
title: "ati x800gt fglrx 7.04 install gdm wont start blank screen keyboard lights flash."
date: 2007-06-26
forum: General Help
---

### Post by Wil0 on 2007-06-26
when i try to boot ubuntu 7.04 i dont get a loading screen and gdm refuses to start, the screen goes black then blank asif no monitor input, the keyboard lights flash also.
however i can boot into recovory mode and startx as root, this works fine, as soon as i try and start gdm in the console though it crashes and the same happens, blank screen and flashing keyboard... basically gdm wont load, but why?
whats going on? 
ive uninstalled and reinstalled gdm with no luck...
help?

---

### Post by charleseddy on 2007-06-27
So what was happened when this occurred?  I assume just after a reboot, but do you remember any software that was installed, settings changed, etc.?  For starters, I'd replace the xorg.conf file and see how that works.

---

### Post by Wil0 on 2007-06-27
this was just after the install...
how can i replace the xorg.conf file just do a reconfigure?

---

### Post by applefreakpeeps on 2007-07-03
what motherboard are u using? we had a similar problem with mcp51 boards and ati graphics which was fixed fro x86 kernels in the 8.38.6/7 release

---

