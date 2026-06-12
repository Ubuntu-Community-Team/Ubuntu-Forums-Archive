---
title: "[SOLVED] Top Bar problem"
date: 2008-05-24
forum: General Help
---

### Post by titico on 2008-05-24
Hello
I've been trying to set all the menus in the top panel to look transparent but i can't do it...

any help is appreciated. 

[IMG]http://img389.imageshack.us/img389/7218/leopardbarws0.png[/IMG]

---

### Post by Genius314 on 2008-05-24
That's part of the theme you're using.
Go to /home/username/.themes/ThemeName/gtk-2.0 (press ctrl+h to show the .themes folder), and look for the image used for the panel. Backup the image, and edit the original so that it is completely transparent.
Now go to a terminal and type:
```
killall gnome-panel
```
This will close and reopen the new panel, which will refresh the theme. You should see the bar completely transparent now.

Hope that helps. :)

---

### Post by titico on 2008-05-25
Thanks, it worked, but i didn't set the images to transparent, I only removed the panel background images, and it's done.

Thank you.

---

