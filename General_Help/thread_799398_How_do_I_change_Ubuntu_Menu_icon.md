---
title: "How do I change Ubuntu Menu icon?"
date: 2008-05-19
forum: General Help
---

### Post by mishathegoat on 2008-05-19
Hiya everyone! I'm having some difficulties with my Ubuntu Menu and I'm hoping someone can help me out. I've tried a few different things and none seem to work.. (Using Gutsy)

I've tried using:
```
sudo gconf-editor
```
and navigated to "apps>panel" but there is no "objects".
So instead I navigated to "apps>panel>default_setup>objects>menu_bar" and checked "use_custom_icon" and changed to value of "custom_icon" to "home/misha/Goat-48x48.png" (I've used png files for the menu icon before so I know the problem is not the extension)

The theme I'm using is custom:
Controls: Clearlooks
Windowborder: Human
Icons: Mist

So I'm not sure which directory to use to replace the icon..

---

### Post by i-am-me on 2008-05-19
I'm not sure if it'll work, but go to /usr/share/icons/(Icon theme)/(Whatever size, if not all of them)/places. After that create three copies (or links) of the desired image named: start-here-debian.png, start-here.png, and gnome-main-menu.png. It might not let you do this (I've tried modifying icon themes before, doesn't seem to work. You could try creating an identical icon theme in a new folder, but with a new name and the icons for the menu), but I'm pretty sure these are the icons you're looking for, if not, then I don't know.

---

### Post by angry_johnnie on 2008-05-19
In order for the 'custom icon' option in gconf-editor to work, you would have to be using main menu instead of menu bar (if that makes sense... right click on the panel and choose add to panel, you'll see both main menu and menu bar).

This is what gconf-editor has to say about 'custom icon'

> If true, the custom_icon key is used as a custom icon for the button. If false, the custom_icon key is ignored. This key is only relevant if the object_type key is "menu-object" or "drawer-object"

Menu bar is identified as object type menu_bar.

I guess it would work if you went to /usr/share/icons/your-icon-theme
and replaced anything named **distributor-logo** with the icon you want, maybe.

---

### Post by mishathegoat on 2008-05-23
Here is what I resorted to doing...

Only some of the icon themes (in /user/share/icons/(icon theme)/(size x size)/places) have the ubuntu menu icon available for me to change. So I changed the menu icon in the "human" theme (since **has** a menu icon in there).

The actual icon that I changed was:
/user/share/icons/human/(size x size)/places/start-here.png

---

