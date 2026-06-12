---
title: "Installed gnome-panel from source, lost applet icons!"
date: 2007-08-07
forum: General Help
---

### Post by Mr. Picklesworth on 2007-08-07
I decided to play around with gnome-panel (I realized that it could be *easily* used to do desklets in a style like Vista, just as long as some panels are not raised on top of windows and do not create struts. Little did I know, of course, this would involve some really scary stuff with Xlib and atoms and humungous standards documents...).

When it came to testing my changes, it became very difficult to be running the right panel! As soon as I tried killing the gnome panel, the gnome session would restart it instantly. I had to execute my panel immediately after killing the gnome panel, and this felt ugly! (It also caused me to be spammed by messages from the other panel telling me it was shutting down).
Thus, to solve this, I (foolishly) decided to 'make install' my altered panel so it would replace the existing gnome panel installation!

When it came to reverting to the normal (not in shambles :P) version, things went goofy :( Not disastrously goofy (I am sure someone "gets" this stuff!), but goofy for me.
After 'make uninstall'ing my changed gnome-panel, then using 'aptitude reinstall gnome-panel gnome-panel-data', certain applets have broken icons or strange defaults. The "Force Quit" applet's icon is broken (big red X), the clock applet's default display is just the time and it does not have an icon in the Add To Panel window. The following icons also do not have icons in the Add To Panel window:

-Fish
-Drawer
-Force Quit
-Window List
-Window Selector
-Workspace Switcher
-Notification Area
-Separator

Of course, I want these icons back. I have tried removing everything to do with the panel via apt-get remove, then reinstalling via apt-get install, I have tried aptitude (as previously), but the icons remain the same.
I have vague memories of similar things happening, and I imagine there is a sensible explanation to do with how package management works... Trouble is, I don't know it. Thanks in advance, anyone that can help!

---

