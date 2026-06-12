---
title: "Wine System Tray is detached on startup"
date: 2008-05-30
forum: General Help
---

### Post by danclarke on 2008-05-30
Hi.  I'm running a small window's program using Wine which puts an icon in the system tray.  This works fine, however I want this program to run at startup.  I've put it in the session manager autostart thing.  This now runs at startup - but it's being run before the main gnome system tray is created.  So I'm getting the 'wine system tray' appearing detached from the main system tray at startup.  If I close my application, the wine system tray disappears (as that's the only icon on it), and re-running it does as it should do (putting it in the main system tray).

Is there any way around this?

Cheers,
Dan.

---

### Post by Zorael on 2008-05-30
I get this with KDE's update notifier (adept_notifier) upon starting Compiz.

There's a bit of work involved, but you could write a script that delays the start of your launcher icon, to give (compiz and) the Gnome tray time to load properly.
```
#!/bin/bash

sleep 5		# modify this number as you please; it's in seconds. perhaps 10 would be a better number? depends on how fast your system loads. experiment.
winelauncher &	# I'm just guessing this is the name of the launcher itself, since I don't have it
```
Save it someplace - anywhere, really - and make it executable by right-clicking it in Nautilus. Or by entering this in a terminal.
```
$ chmod +x *<script name>*
```
Change your Sessions entry to point to this script instead, log out, log in, see if it worked. If not, increase sleep duration, try again.

If you place the script in [FONT="Courier New"]/usr/local/bin/[/FONT] it will be available by just entering its name in a terminal, but then you'd need root permissions to save it there. The fact remains that it can be located anywhere as long as the Sessions entry reflects this.

---

