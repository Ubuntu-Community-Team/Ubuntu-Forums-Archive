---
title: "Toggle Fullscreen"
date: 2007-04-06
forum: General Help
---

### Post by CubicVirtuoso on 2007-04-06
I have a simple question. When I load Half-Life 1 through Wine (or steam) it goes into fullscreen mode, but I can still see Ubuntus task bars on the top and bottom. Is there a way I can make Halflife 1 go over top of those task bars... or somehow toggle them on and off. Thanks for the help!

---

### Post by T3h_Dohtem on 2007-04-25
I am having this same problem, it happens in World of Warcraft ( WoW ) also. The problem just showed up, I have been playing both games flawlessly for months until some recent updates. I don't know if it was the X11 drivers on the wine drivers, but after both of them, I cant use a real fullscreen anymore. Anyone figured this one out yet?

---

### Post by oerz on 2007-04-26
> **T3h_Dohtem said:**
> I am having this same problem, it happens in World of Warcraft ( WoW ) also. The problem just showed up, I have been playing both games flawlessly for months until some recent updates. I don't know if it was the X11 drivers on the wine drivers, but after both of them, I cant use a real fullscreen anymore. Anyone figured this one out yet?
Me too!
I just installed WoW on my Laptop (by copying a windows installation and following a HOWTO). It seems to be working fine except it runs in something between a window mode and a fullscreen mode:
The screen resolution goes to 800x600, I see the WoW login screen plus the Gnome Taskbar. When I move the mouse to the border of the screen, it moves so that I can now see the terminal or the browser or whatever is next to the WoW-"window".

Any ideas?
Thanks in advance,
oerz

---

### Post by SilverSkulls on 2007-04-26
I have the same troubles.
I used to be able to run Counter-Strike Source and Starcraft without any hitches.  After a recent update, I am unable to play them due to this problem:
My gnome desktop resolution is 1024x768.   When the application starts, the resolution that my monitor displays goes down to the size that the program is outputting at (800x600 for Starcraft or 1024x768 for CS:S).   I can see the application's window , but it has the gnome taskbar over top of it.  When I move my cursor to the bottom or right side of the screen, I discover that I can traverse the portion of my desktop that the wine application is not currently using up, and use it as normal.
In summary:  The physical resolution that my monitor outputs at goes down to game-size, but the logical resolution stays desktop-size.  The wine application only fills up the portion of the desktop that its resolution is at.  I can change the position on my desktop by moving the cursor to the edges of the screen.  This makes playing these games hard.

Thanks in advance,
Silverskulls

---

### Post by oerz on 2007-05-01
wine-0.9.36 has resolved the problem.
Thanks!

---

