---
title: "Theme Manager problem"
date: 2006-08-26
forum: General Help
---

### Post by Dropknee on 2006-08-26
The themes not apply correctly, this is what appear in terminal

```
(gnome-theme-manager:32151): Gtk-CRITICAL **: gtk_icon_info_get_filename: assertion `icon_info != NULL' failed

(gnome-theme-manager:32151): Gtk-CRITICAL **: gtk_icon_info_free: assertion `icon_info != NULL' failed

(gnome-theme-manager:32151): Gtk-CRITICAL **: gtk_icon_info_get_filename: assertion `icon_info != NULL' failed

(gnome-theme-manager:32151): Gtk-CRITICAL **: gtk_icon_info_free: assertion `icon_info != NULL' failed

```

and this appear when try to apply a Control theme
```
/home/username/.themes/LiNsta3/gtk-2.0/menubar-custom.rc:22: Unable to locate image file in pixmap_path: "Menu-Menubar/menubar-black.svg"
/home/username/.themes/LiNsta3/gtk-2.0/menubar-custom.rc:25: Background image options specified without filename
/home/username/.themes/LiNsta3/gtk-2.0/menubar-custom.rc:31: Unable to locate image file in pixmap_path: "Menu-Menubar/menubar-black.svg"
/home/username/.themes/LiNsta3/gtk-2.0/menubar-custom.rc:34: Background image options specified without filename
/home/username/.themes/LiNsta3/gtk-2.0/menubar-custom.rc:22: Unable to locate image file in pixmap_path: "Menu-Menubar/menubar-black.svg"
/home/username/.themes/LiNsta3/gtk-2.0/menubar-custom.rc:25: Background image options specified without filename
/home/username/.themes/LiNsta3/gtk-2.0/menubar-custom.rc:31: Unable to locate image file in pixmap_path: "Menu-Menubar/menubar-black.svg"
/home/username/.themes/LiNsta3/gtk-2.0/menubar-custom.rc:34: Background image options specified without filename

```

Any help pls

---

### Post by Michalxo on 2008-04-26
Same problem here.
I think it's themes' fault, because other don't to that. 

Hmm... just looked on that, and I thing there is a little typo in 
~/.themes/LiNsta3/gtk-2.0/menubar-custom.rc

just edit 2 lines (in my case) from
file		= "Menu-Menubar/menubar-black.svg"

to this:
file		= "Menu-Menubar/menubar-black.png"

It works for me..

cheers

---

