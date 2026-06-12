---
title: "Help, Ubuntu Acting Up."
date: 2008-02-22
forum: General Help
---

### Post by RyanJSull on 2008-02-22
There are a ffew errors that started at the same time, i think they may be connected.  Can somebody help me make sens of what is going wrong, and how I can fix it?  Problems incluse a random 10-20 second freeze when booting up just after the wallpaper loads, mouse can move but everything is unresponsive.  When i run sudo nautilus i get the following error message:
Initializing gnome-mount extension

** (nautilus:2164): WARNING **: Cannot extract frame (0, 0) from the grid

Segmentation fault (core dumped)

The Seg fault doesn't normally happen, but it happened this time.  Nautilus loads after it does this.
When I am in Nautilus as root, if i open a file, gedit produces the same error:
** (gedit:5503): WARNING **: Cannot extract frame (0, 0) from the grid
.
As a side note, I am running a laptop and i notice about every 3-4 seconds the wifi light flashes and the harddrive light flashes just  after the wifi.  I am using a wired connection, so I wouldn't expect my wifi light to flash.  I looked up the harddrive light and it said to check it with : 
sudo smartctl -a /dev/sdb | grep Load_Cycle_Count
When i do this, my load count is not increasing at any noticable rate, so I think it's not causin any problems.  If anyone has any info on why it takes forever to boot, or why theres the Cannot extract frame error that would be appreciated.  Any help would be appreciated.

---

### Post by RyanJSull on 2008-02-22
Oh, and gksudo clears up the error message that it gets with sudo, however if i still try to open a file with gedit as root, it still gives the error message.  This error does not happen if i just run nautilus from the terminal.

---

### Post by RyanJSull on 2008-02-24
Fixed it, apparantly a icon set i downloaded had misnamed icons or something cause it caused the problem... switch icon themes and everything works fine.  Pity tho, the icons were really nice.

---

