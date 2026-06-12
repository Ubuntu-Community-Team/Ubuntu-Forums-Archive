---
title: "[ASUS K56CB] laptop heats up while performing basic tasks"
date: 2014-08-23
forum: General Help
---

### Post by Mcgloud on 2014-08-23
Hello everybody,
 
Recently I installed Ubuntu 14.04.1 on my ASUS K56CB laptop which I bought last october. The laptop has a Intel HD graphics and a Nvidia GT 740m card. Those two are configured properly in Ubuntu: I'm using the suggested Nvidia driver with Intel graphics as my PRIME profile. 
 
The only thing that is bugging me, is, as the title explains, that my laptop heats up for no reason while doing basic tasks. While doing some shockwave flash based games in Chrome, searching for files and stuff in the Dash the fan is going somewhat faster, louder and hotter. 
 
I really don't know what's causing this.
 
Complete list of specs:
ASUS K56CB
i5 3777U 
6gb ram
Nvidia GT 740m using latest Nvidia drivers 
 
 
Hopefully someone can help me solve this damn issue so I can finally enjoy using Ubuntu all the time!

---

### Post by Cliff_Simonds on 2014-08-24
I've been using an Asus X54C (K54C bios) for about 3 1/2 years myself. Chrome is a resource hog anyhow. That said, until I turned off the online searches in the dash and installed dconf Editor and disabled all scopes, lenses and plugins that searched online (don't need them that's why I have a "secure" browser), my fan was revving up like a dragster when searching in the dash. I use the dash like a start menu in windows 7 and not like it'll be with windows 9 and cortana. Way too resource intensive and not needed.

---

### Post by Mcgloud on 2014-08-24
I have used the Top command in a terminal Window and it is telling me that compzi and Xorg are the biggest resource hogs.


How do I lower this?

---

### Post by Cliff_Simonds on 2014-08-24
> **Mcgloud said:**
> I have used the Top command in a terminal Window and it is telling me that compzi and Xorg are the biggest resource hogs.


How do I lower this?
You don't. They're your desktop environment(like windows desktop manager) it's normal and and they should always be near or at the top of the list. Xorg is basically the X window system used in linux. It's the base of the graphical environment for your computer. And "
(taken from Compiz README)
Compiz is  an OpenGL compositing manager that use GLX_EXT_texture_from_pixmap for  binding redirected top-level windows to texture objects. It has a  flexible plug-in system and it is designed to run well on most graphics  hardware.
Okay, this description isn’t really meaningful. In a  nutshell, Compiz is a compositing manager, which means that it enhances  the overall user interaction by adding fancy effects to your windows,  from drop shadows to awesome desktop effects like the [Desktop Cube]("http://wiki.compiz.org/Plugins/Cube") or the [Expo]("http://wiki.compiz.org/Plugins/Expo") view.
Compiz  can also be a window manager, which means that it is the software  between you and your desktop apps. It enables you to move or resize  windows, to switch workspaces, to switch windows easily (using alt-tab  or so), and so on."

See [this]("http://askubuntu.com/questions/227950/how-to-remove-the-ubuntu-software-center-suggestions-from-the-dash") to turn off unneccesary "More Suggestions" in the dash, and [this]("http://ubuntuforums.org/showthread.php?t=2224883") to shut down the shopping scopes, then your dash searches should be quicker and use alot less resources.  For internet I use firefox with my  (from windows partition) chrome bookmarks inported. 
All in all my X54C doesen't over heat with ubuntu, but I have upgraded to 8gb ram and a 256gb ssd and ssd's don't heat up as quick as hdd's.

---

