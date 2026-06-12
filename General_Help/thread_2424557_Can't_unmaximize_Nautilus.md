---
title: "Can't unmaximize Nautilus"
date: 2019-08-10
forum: General Help
---

### Post by whairst on 2019-08-10
I'm running Ubuntu 14.04. Nautilus ("Files") has somehow become super-maximized, even hiding the Unity launcher. The usual close, minimize, and maximize buttons aren't there (or possibly offscreen?) I can alt-space and minimize, but maximize/unmaximize, move, and resize do nothing. Super-middleclick does nothing in Nautilus. I can close it, or alt-tab to a different program to get to the launcher, but I can't find any way of turning it back into a normal window. Help!

---

### Post by guiverc on 2019-08-10
Ubuntu 14.04 LTS was from 2014-April (thus 14.04) and came with 5 years of supported life, is now EOL unless you switched to 14.04 ESM supported by Canonical (for fee with Ubuntu Advantage).  I would suggest you consider release-upgrading to 16.04 LTS asap for security reasons.

*Sorry I can't help with your real problem, I'm neither a gnome or unity user - you'll have to wait for someone else*

---

### Post by whairst on 2019-08-10
Yes, I am aware that 14.04 is EOL. I'm trying to put off a full hardware replacement for a bit. In the meantime, it's still far more secure than running XP (which is what this particular hardware was bought for).

Any ideas on the issue with Nautilus?

---

### Post by sevendogs1337 on 2019-08-10
Is the titlebar visible?

---

### Post by Holger_Gehrke on 2019-08-10
Alt-drag should work. Position the mouse pointer inside the window, hold the 'Alt'-key, hold the left mouse button, move the mouse to move the window. This way you should be able to move the window so that it's borders can be grabbed to resize the window.

Holger

---

### Post by whairst on 2019-08-10
I'd say there's no titlebar. This is what the upper left corner of my screen looks like. Nautilus goes all the way to the corner of the screen, unless I alt-tab to a different program.
[ATTACH=CONFIG]283773[/ATTACH]

Alt-drag doesn't seem to do anything in any program. Super-drag works in other programs, but not Nautilus.

---

### Post by mc4man on 2019-08-10
Try this
install dconf-editor if not already
Open a terminal & run
```
killall nautilus
```
Then open dconf-editor, navigate to org > gnome > nautilus > window state
Set the geometry string to default, i.e highlight geometry > click button on bottom, Set to Default
Also set maximized to false (the default

Close dconf-editor, open nautilus, see..

---

### Post by whairst on 2019-08-10
Yep, that did it. Geometry was set to my screen resolution. Maximized was unchecked, but in bold like it wasn't default. I set both back to default, and everything's the way it should be. Thank you!

---

### Post by mc4man on 2019-08-10
Somehow nautilus got into a fullscreen geometry, probably will remain a mystery as to how as there is no option or binding for that. (typically F11 for apps that support fullscreen
At least now you have the means to correct if it happens again..

---

