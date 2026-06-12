---
title: "Raise most recent window in Ubuntu Gnome 3"
date: 2018-11-15
forum: General Help
---

### Post by mathuhenry2 on 2018-11-15
In Ubuntu 18.04 and 18.10, if two windows of the same program are open and minimized, then clicking on the launcher icon will raise a windows selection tool (replacing program spread). But it won't bring up the most recent window on first click (I always have to choose from the selection window). This slows down rapid switching between windows of different programs. Is it possible to change this behavior? I would prefer to only access program spread if a window is already active when I click on the icon (like the Unity 7 behavior).

Also, is there a setting for scrolling through a programs windows with the scroll wheel?

Thank you!

---

### Post by vanadium on 2018-11-16
> I would prefer to only access program spread if a window is already active when I click on the icon (like the Unity 7 behavior).
This is not possible. The next best option for you would be to set the click behaviour to "cycle-windows". This option will bring the the most recent window of the application in the front. Another click will bring the next window of the application to the front. This allows for quick switching between applications. If you happen to need another window of the same application, click until that one is in the front.

There is a setting to cycle windows on scrolling.

You will find all settings related to the Ubuntu Dock in dconf-editor under org.gnome.shell.extensions.dash-to-dock. You may need to install dconf-editor first because it is not installed by default.

---

### Post by Dennis N on 2018-11-16
Use the alt-tab switcher - it arranges the windows so that the previous one is the first choice. To include windows in all desktops, install the gnome extension "AlternateTab".

---

### Post by vanadium on 2018-11-16
@Dennis N, OP wants to use the dock for task switching. "Alternate Tab" will *not* include windows in all desktops by default.

---

### Post by mathuhenry2 on 2018-11-16
Cycle windows works perfectly for my purposes.

Thank you everyone!

---

