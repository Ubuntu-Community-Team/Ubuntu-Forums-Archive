---
title: "Hopefully a simple fix"
date: 2008-05-20
forum: General Help
---

### Post by djmoore85 on 2008-05-20
Hey yall, quick question on something. How do you increase the size of the icon used for the main menu, I removed the applications/places/system menu on my only taskbar on the bottom of the desktop and replaced it with the Gnome main menu which is simply a Gnome foot icon. I am trying to figure out how to make the icon larger or plug a custom one into its place. Thanks in advance for any help yall.

---

### Post by ad_267 on 2008-05-20
If you right click on an empty space in the panel and select properties then increase the size of the panel, the icon should expand to take up the new height of the panel. Also if you want to replace the icon I think it's called "starthere.png" of "starthere.svg" in most icon sets.

---

### Post by skip mcshwang on 2008-05-20
Not sure if you can set a size independent of the rest of the panel, but you can set a custom icon from within gonf-editor:

0. Run gconf-editor in terminal
1. Navigate to /app/panel/objects
2. Find the object_x with an object_type of "menu-object"
3. Tick "use_custom_icon"
4. Set "custom_icon" value to the image path

---

### Post by djmoore85 on 2008-05-20
Well I looked through all my .icon files, my .theme files and a few others but I cannot for the life of me find my Dropline Neu! icon file to modify the size or edit the foot icon. Now my question is, how do I make a scalable icon through Gimp or Draw maybe? And how do I find where my icon theme is located at?

---

