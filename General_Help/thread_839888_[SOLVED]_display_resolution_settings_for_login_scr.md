---
title: "[SOLVED] display resolution settings for login screen - please help"
date: 2008-06-24
forum: General Help
---

### Post by hurtstotalktoyou on 2008-06-24
Hi, all.

When I install Ubuntu or Xubuntu 8.04, my analog CRT displays are not properly detected.  Running displayconfig-gtk, I see that Ubuntu/Xubuntu thinks I can't have greater than 800x600 resolution.  I have to change the displayconfig-gtk setting from "plug 'n' play" to a generic 1024x768 monitor.  Only then can I change the resolution to 1024x768.

This works for the most part, but the login screen freaks out about it.  Whenever I login or out, Ubuntu/Xubuntu gives me only the left 800 columns and top 600 rows of pixels.  So, I can't see the right 224 columns, nor the bottom 168.  Not only does this look very strange, and therefore annoying, but it cuts off my reboot/shut down options.

```
An illustration:

.......................XXXXX
.......................XXXXX
.......................XXXXX
.......................XXXXX
.......................XXXXX
.............login.....XXXXX
.......................XXXXX
XXXXXXXXXXXXXXXXXXXXXXXXXXXX
XXXXXXXXXXXXXXXXXXXXXXXXXXXX
XXXXXXXXXXXXXXXXXXXXXXXXXXXX

(the X's are cut off, not viewable)
```

I was able to fix this problem on my bedroom rig, because I had nvidia-settings save the proprietary driver settings to the xorg.conf file.  However, I'm currently working with a new rig which does not have a proprietary driver.  It uses integrated i810 graphics, which as far as I know has no program similar to nvidia-settings to go with it.  I've tried manually tinkering with the xorg.conf file, but I haven't found anything that works.  So, I'm at a loss as to how to fix the problem on this system.

Any help would be much appreciated!

---

### Post by hurtstotalktoyou on 2008-06-24
Well, I fixed it, myself.  It turns out that xedit, the program I was using in Xubuntu to change xorg.conf, wasn't saving any of my changes.  Stupid, huh?  I had to use mousepad instead.

For archival purposes, here's the solution.

In Xubuntu:
1.  hit ALT-F2 and run "xterm"
2.  enter "sudo mousepad /etc/X11/xorg.conf"
3.  in the xorg.conf file, change the "virtual 1280 960" line to read "virtual 1024 768".
4.  save and logout (or reboot)

In Ubuntu, this would presumably be:
1.  run terminal
2.  enter "sudo gedit /etc/X11/xorg.conf"
3.  in the xorg.conf file, change the "virtual 1280 960" line to read "virtual 1024 768".
4.  save and logout (or reboot)

Thanks!

---

