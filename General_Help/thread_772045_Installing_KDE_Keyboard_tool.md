---
title: "Installing KDE Keyboard tool"
date: 2008-04-28
forum: General Help
---

### Post by sp3ctum on 2008-04-28
I have ubuntu 8.04, and it's worked out great so far. Even sound worked out-of-the-box, which it didn't do with 7.10.

I've been working on installing all of my old programs back after a complete re-install. Now I again struggle with adding my keyboard layout. Last time it worked when I used not the gnome keyboard layout tool, but the KDE one.
I don't have any recollection of how I managed to install the latter into my system - it just mysteriously appeared. However, it doesn't do so now.

So now I need advice on how to install the KDE keyboard tool (unsure of the name) to manage my keyboards and their layouts with that instead of with the gnome tool that ships with ubuntu.

---

### Post by ozorba on 2008-04-28
Is this any good?

[http://www.ubuntuforums.org/showthread.php?t=124465&page=2](http://www.ubuntuforums.org/showthread.php?t=124465&page=2)

---

### Post by sp3ctum on 2008-04-28
No, I'm afraid it doesn't help.
I don't seem to find any information about installing the kde keyboard tool there. Any more ideas? :/
It's odd that I don't know how it got fixed the last time.

---

### Post by sp3ctum on 2008-04-29
bump.
I still need help with this issue. :)

---

### Post by sp3ctum on 2008-05-01
bump.
Anyone got any ideas? Happy may day btw :)

edit: I think this is in the wrong place. Mods, can you move this to a proper place?

---

### Post by sp3ctum on 2008-05-01
I tried installing kcontrol in an attempt to get access to keyboard layout settings, but it was not included in the package.

When trying to install my das layout like it's supposed to be, it shows up in the menu, but when I try to close the gnome keyboard layout handler, it displays two of these error message windows:

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10400090

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd




So.. Either a fix for that or the KDE keyboard layout tool is what I need, I think.

---

### Post by sp3ctum on 2008-05-01
I solved my own problem.
Here's how:

- the command setxkbmap let me change my layout, but the keyboard manager that's default in ubuntu wasn't too happy about that, and kept whining about the previously mentioned error. I couldn't change the layout the official way.
- I made two scripts: one for activating my das keyboard layout, and the other activating the standard Finnish qwerty layout. I added the das one to the startup programs, and added them both to the panel as well for quick execution.

A nice workaround, since not only does the new keyboard layout work, this time all my hotkeys for window managing work as well.

Edit: A script that changes the keyboard layout looks like this:

#!/bin/bash
setxkbmap fi

Then save it as qwerty.sh anywhere you want, and run the command chmod +x qwerty.sh to change its rights so it can be executed.

---

