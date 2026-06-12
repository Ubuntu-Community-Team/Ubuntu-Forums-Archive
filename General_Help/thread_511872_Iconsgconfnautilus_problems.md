---
title: "Icons/gconf/nautilus problems"
date: 2007-07-28
forum: General Help
---

### Post by Go_Bucks on 2007-07-28
Hi all,

I have searched throughout the forum and have thus far been unable to find a similar problem to this, and thus, a resolution. Since my install a month ago I have not had any icons on the menu bar. The icons are present on the system as I can select them in System>Preferences>Main Menu. The first screenshot below shows what I mean.

I gathered from other similar (but not the same) questions that it could have something to do with nautilus desktop configuration in gconf. Several posts have stated you can make adjustments in the configuration editor under apps>nautilus>desktop. The problem is, apps>nautilus>desktop does NOT exist on my system (see second screenshot). I tried reinstalling nautilus from synaptics with a reboot afterward but there was no change.

Any ideas...I hope? I have been unable to get help on every issue I've posted on thus far and eventually figured them out myself, but this one ain't going away without the assistance of someone more knowledgeable than I.

Thanks.

---

### Post by mcduck on 2007-07-28
Have you already looked at System/Preferences/Menus & Toolbars? Make sure "Show icons in menus" is enabled.

---

### Post by Go_Bucks on 2007-07-28
Yes... and I just double-checked it. Show icons in menus is checked. But what about the absence of apps>nautilus>desktop? I understand you can control a lot of behaviors there and I have no such thing.

---

### Post by tbroderick on 2007-07-28
Have you tried deleting your /home/username/.gnome2 and .gconf folders ? Try that and logout. Also, have you used any window manager or desktop other then GNOME and set a theme with something other then gnome-theme-manager?

---

### Post by Go_Bucks on 2007-07-28
> **tbroderick said:**
> Have you tried deleting your /home/username/.gnome2 and .gconf folders ? Try that and logout. Also, have you used any window manager or desktop other then GNOME and set a theme with something other then gnome-theme-manager?

I tried your first suggestion and all that did was destroy the function of my mouse. The icons were still not present so I restored the files. I have not used any other window manager or desktop.

---

### Post by mcduck on 2007-07-28
> **Go_Bucks said:**
> Yes... and I just double-checked it. Show icons in menus is checked. But what about the absence of apps>nautilus>desktop? I understand you can control a lot of behaviors there and I have no such thing.

It's strange that the option is missing, but it has nothing to do with your menu icons. Nautilus is the file manager in Gnome, and also handles your desktop, while that menu is applet for Gnome-panel.

---

### Post by Go_Bucks on 2007-07-28
> **mcduck said:**
> It's strange that the option is missing, but it has nothing to do with your menu icons. Nautilus is the file manager in Gnome, and also handles your desktop, while that menu is applet for Gnome-panel.

Agreed. So, does anyone have any idea how to get apps>nautilus>desktop back?

---

### Post by Go_Bucks on 2007-07-28
So back to the icons, I now know thanks to mcduck that the portion for which the icons is missing is part of gnome - panel. Please see attached image of gconf below. Is "hide-button-pixmaps-enabled" the problem? If so, how do I fix it? There is no check box, and I don't want to start messing with things without someone telling me it is OK.

---

### Post by Go_Bucks on 2007-07-29
bump for help

---

