---
title: "Terminal keeps moving to the top of the screen"
date: 2012-10-27
forum: General Help
---

### Post by *^kyfds( on 2012-10-27
As i'm not particularly good at remembering terminal commands, most of the time i just end up copying them from the internet.

This bug makes this almost impossible, as 9 times out of 10, when i'm switching back and forth from terminal, the terminal window will shoot up, and subsiquently get stuck at the top of the screen, behind the taskbar.

Is there known fix for this bug?
(please bear in mind i'm still not massively familiar with the layout of the ubuntu filesystem, so running commands using files may be a slow process.)

I'm running a dell 1018 mini netbook, with ubuntu 12.10, and unity.

If this issue can't be worked around, a keyboard shortcut to centre a window to the middle of the screen would be  very useful too.

Any help is appreciated,

Thehumorouscheese.

---

### Post by cwsnyder on 2012-10-27
"That isn't a bug, it's a feature!" Unity, with its 'global menu' system assumes that any application is the only application running, in full screen, with the menu in the top panel.

I would recommend using the Alt-Tab key combination to switch between open windows and live with that, or switch to a different desktop.

---

### Post by kherring7383 on 2012-10-27
If your running Unity, then you also have Compiz installed that handles the desktop environment such as where windows are places on the desktop when an app is opened.

By default, Compiz uses what is called Smart Windows Placement which generally opens everything in the upper corner of the desktop.

If you have never used Compiz, you may have to install Compizconfig-settings Manager from Synaptic. Once installed run the manager and look for the  Windows Placement option and change it to Centered.

Hope this helps.

---

### Post by mikewhatever on 2012-10-28
> **Thehumorouscheese said:**
> As i'm not particularly good at remembering terminal commands, most of the time i just end up copying them from the internet.

This bug makes this almost impossible, as 9 times out of 10, when i'm switching back and forth from terminal, the terminal window will shoot up, and subsiquently get stuck at the top of the screen, behind the taskbar.

Is there known fix for this bug?
(please bear in mind i'm still not massively familiar with the layout of the ubuntu filesystem, so running commands using files may be a slow process.)

I'm running a dell 1018 mini netbook, with ubuntu 12.10, and unity.

If this issue can't be worked around, a keyboard shortcut to centre a window to the middle of the screen would be  very useful too.

Any help is appreciated,

Thehumorouscheese.

That's rather strange indeed, and obviously isn't a feature of any kind.  Do you know if there is a bug report? Have you filed one?

---

### Post by *^kyfds( on 2012-10-28
I've had a look for one, and i can't seem to find one, so i'm filing one now.

I'll attach a screenshot in a few minutes.

---

### Post by *^kyfds( on 2012-10-30
I'm trying to get a screenshot but for some reason it won't seem to do it now...

Anyway, it's still a problem as it happened with my firefox downloads window a few seconds before i closed it.

---

### Post by mikewhatever on 2012-10-30
Can you take a screenshot of the download window.

---

### Post by diagpope on 2012-11-30
I found out that this placement on top of the desktop can be disabled via:
Application->System Tools -> Preferences -> CompizConfig Settings Manager

Then in Window Manager unselect the tick from "Place Windows" or Select Place Windows and on the left side deselect under Use This Plugin the tick for "Enable Place Windows"

---

