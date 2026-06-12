---
title: "Gnome-main-menu V2 icon"
date: 2007-03-11
forum: General Help
---

### Post by DaMasta on 2007-03-11
I know how to change the old menu's icon. I installed main-menu version 2 and it uses the computer icon with the word computer next to it. I dug around in gconf-editor and couldn't find anything.

---

### Post by ciscosurfer on 2007-03-11
> **DaMasta said:**
> I know how to change the old menu's icon. I installed main-menu version 2 and it uses the computer icon with the word computer next to it. I dug around in gconf-editor and couldn't find anything.I don't think that gconf-editor makes note of the location or names of currently set icons.  Rather, I believe they are set /usr/share/icons or /home/<username>/.icons

Look for an icon name called start-here.svg or start-here.png ... many icons will actually link to this icon name for the main menu icon.

---

### Post by DaMasta on 2007-03-11
The start-here icon is for the regular main menu. This is for the new version. It's a computer icon with the word computer next to it.

---

### Post by DaMasta on 2007-03-13
Bump

---

### Post by ardchoille42 on 2007-03-13
Instructions for changing the Main Menu icon are at the bottom of the first post [here]("http://ubuntuforums.org/showthread.php?t=342060").

Instructions for using the custom Main Menu icon:
1) Right-click the panel and choose "Add to Panel"
2) Add the Main Menu panel applet
3) Open gconf-editor and go to /apps/panel/objects/object_X
where "x" is the number of the Main Menu panel applet, it was 0 on my Dapper computer.
4) Enter a path for the custom button icon in the '[COLOR="Red"]custom_icon key[/COLOR]'
5) Check the box next to the '[COLOR="Red"]use_custom_icon[/COLOR]' key
The Main Menu icon should change immediately, but you might need to 'killall gnome-panel'.

This is for changing the menu icon of the Main Menu panel applet. Is that what you wanted?

---

### Post by DaMasta on 2007-03-13
Thank you. Unfortunately, that only works for the old main menu icon.

---

