---
title: "Unable to load desktop"
date: 2014-01-30
forum: General Help
---

### Post by charlescarroll1 on 2014-01-30
I recently installed the Gnome desktop via the Software Center to play around with. I realized it wasn't for me and removed it. Later that day I was trying to figure out how to disable sleep when closing my laptop lid (with no success). I logged out and realized that Gnome was still on the list of available desktops. I thought that was odd since I removed it, but selected it to see if I was able to close my laptop lid without putting my system to sleep in that desktop environment. 

Nothing loaded - all I see is my wallpaper. Well, this is lame. I restarted my system, the Xubuntu logo appears, and then a black screen with the X cursor. Nothing loads. I tried a few times with the same results. 

I need to figure out a way to switch back to the xfce desktop, but can't since I have no desktop to open settings.

I can boot into a command prompt via GRUB, but I don't know what commands I would need to enter to switch the default desktop environment. Does anyone have any suggestions?

---

### Post by robin7 on 2014-01-30
The command to enter is 
```
 startx 
```

That should get you to a graphical interface.  If your "session" is Xubuntu (which it should be), you can *right*-click anywhere on the desktop to bring up a menu.  Select **Settings > Settings Manager** and use the tabs there to set up your new defaults.

---

