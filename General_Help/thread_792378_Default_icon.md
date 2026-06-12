---
title: "Default icon?"
date: 2008-05-12
forum: General Help
---

### Post by Mchl923 on 2008-05-12
I have chosen some icon images myself, but now I want my firefox icon to be the theme default, how do I do this?

---

### Post by BandD on 2008-05-14
Let me see if I understand you correctly...

You have a "custom" firefox icon that you want your current icon theme to use instead of the "default" firefox icon right?

The fix will depend a little bit upon what type of image the icon is.  Is it a .svg or a .png?

If it is a .svg navigate to the folder where your current icon theme is stored (usually either in /home/USER/.icons/CURRENT_ICON_THEME/  or  /usr/share/icons/CURRENT_ICON_THEME/) and look for a folder called "scalable".  Then look for a folder inside of that called "apps", name the icon "firefox.svg" and save it in that folder (i.e.../CURRENT_ICON_THEME/scalable/apps/firefox.svg)

Alternatively you can navigate to /usr/share/pixmaps/ and save either the .svg or the .png there as either "firefox.png" or "firefox-3.0.png" for firefox 3.0b5 (if the image is a .svg then change .png to .svg).

You'll need root privileges for that.  So if your comfortable with the command line you can just use the mv command.  Or if you'd like to use a GUI then type this in a terminal:

```
gksudo nautilus
```

That will open a Nautilus window with root privileges... so BE VERY CAREFUL!!!!!!

That should do the trick.  

Let me know if you have any questions.

---

