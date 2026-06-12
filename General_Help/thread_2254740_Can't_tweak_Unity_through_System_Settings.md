---
title: "Can't tweak Unity through System Settings"
date: 2014-11-29
forum: General Help
---

### Post by Shinsekai_Yori on 2014-11-29
I was looking through some of the settings in CompizConfig Settings Manager, when I messed something up and pressed "reset to defaults" for the profile. That then removed all the UI from windows, so I created a new profile that brought everything back to default. However, now any changes to the desktop environment (such as icon size, wallpaper, theme, etc...) done in System Settings or Unity Settings doesn't do anything, I can only modify it via CCSM. Only changing the window menu position and adding Show Desktop to the launcher works.

I've tried resetting it via dconf reset -f /org/compiz/, setsid unity, and unity --reset-icons, but that didn't do anything. Also, now when restarting Unity the top right of the menu bar, notifications, my media keys, and the window menus disappear and only work again after restarting my computer.

---

### Post by mc4man on 2014-11-29
That was an unfortunate choice (to click on reset defaults) as it appears to be totally bugged.

You can reset all the ubuntu session (unity) default enabled plugins manually but first try this - 
open a terminal & move to side of screen
Open ccsm > Preferences & set the profile back on unity
close ccsm
Then in the terminal run those 2 commands - 
dconf reset -f /org/compiz/
setsid unity

If that proves problematic then for starters open ccsm  > Preferences & set the profile back on unity
Then click on the Ubuntu Unity plugin button & re-enable it
Back in the main plugin listings also enable if not already - 
Composite
OpenGl
Desktop Wall
Viewport Switcher
Animations
Fading windows
Png
Compiz Library Toolbox
Regex Matching
Mouse position polling
Session management
Workarounds
Scale
Move window
Resize window
Place window
Snapping windows
Grid
Maybe a couple of others. 
It would be far better if the first thing I mentioned worked as doing manually you may have to deal with some choices regarding "Conflicts"

---

