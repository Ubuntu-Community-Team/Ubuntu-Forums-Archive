---
title: "Custom action &quot;Set as Wallpaper&quot; in Thunar"
date: 2013-08-03
forum: General Help
---

### Post by Bladeforce on 2013-08-03
Hi I am trying to add the action set as wallpaper in Thunar file manager when i right click an image file as the default action that comes with thunar doesn't work.

  I have added this line to the custom command but it just changes any selected image to the default ubuntu wallpaper. Not only this is there any way to make it appear scaled by default and also add custom options to extract to/add to archive using archive manager?

gsettings set org.gnome.desktop.background picture-uri %f

  I am running 13.04 with unity desktop, thanks for any help

---

### Post by adec2 on 2013-11-26
When setting up your custom action enter

gsettings set org.gnome.desktop.background picture-uri file:///%f

in the command field and in appearance conditions select image files. Enter "Set As Ubuntu Wallpaper" without the quotes in your name field. Now when you right click an image file you will get an option to "Set As Ubuntu Wallpaper"

---

