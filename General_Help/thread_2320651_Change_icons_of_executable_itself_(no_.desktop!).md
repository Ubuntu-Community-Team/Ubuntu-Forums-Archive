---
title: "Change icons of executable itself (no .desktop!)"
date: 2016-04-16
forum: General Help
---

### Post by SamInside on 2016-04-16
I want to change the infamous VLC icon with something better. I edited */usr/share/applications/vlc.desktop* and I changed the *Icon* entry.
This works for the *Whisker Menu* and every other window of *Xfce*.
However, in the *Window Buttons* part of the panel (where active windows are listed) and in the *Indicator plugin* (system tray), the standard VLC icon is shown.
I guess this is because the icon is hardcoded in the binary executable?

If that's the case, I guess I need a software like *Resource Hacker* for Windows: what program do you suggest for linux? (please don't say *Wine*, thanks).

If that's not the case, then what steps should I take?

---

### Post by bapoumba on 2016-04-16
Not that sure as I am not on xubuntu but may be close enough.

If you right click on the panel icon, do you have a properties tab ? If so, click on the icon it shows and you'll have the path to this icon itself.
Here it is located in /usr/share/icons/hicolor/48x48/apps/vlc.png and I could change it.
No idea (yet) where the active window icon is :)

Edit [https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/530797](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/530797) ?
Edit 2 : would not the active window icon come with the theme ?

---

### Post by Le3eVolfoni on 2016-04-16
I never experienced Xubuntu but this worked for me in Ubuntu. The icon in the panel is possibly not the scalable icon, the one you changed. In your icon folder (in my case /usr/share/icons) find your icon theme, and inside you should find or a folder called "panel" or "apps". In these folders icons are separated per size. Your VLC icon should be somewhere there.

In Ubuntu it is possible to change these icons with nautilus as root using gksudo nautilus. It should work in Xubuntu, change nautilus by your file manager and the process should be the same. Do a backup of your icon folder before you touch anything.

Sorry I can't be more specific but I hope it helped.

---

### Post by SamInside on 2016-04-16
Thanks to you both.

I did:
```

$ find /usr/share/icons/ -name "*vlc*"
```
and I got:
```

/usr/share/icons/hicolor/16x16/apps/vlc.xpm
/usr/share/icons/hicolor/16x16/apps/vlc.png
/usr/share/icons/hicolor/48x48/apps/vlc-xmas.png
/usr/share/icons/hicolor/48x48/apps/vlc.png
/usr/share/icons/hicolor/256x256/apps/vlc.png
/usr/share/icons/hicolor/128x128/apps/vlc-xmas.png
/usr/share/icons/hicolor/128x128/apps/vlc.png
/usr/share/icons/hicolor/32x32/apps/vlc-xmas.xpm
/usr/share/icons/hicolor/32x32/apps/vlc.xpm
/usr/share/icons/hicolor/32x32/apps/vlc.png
```

Looks like I am on the right path. I'll try changing these icons and I'll report back.

---

### Post by SamInside on 2016-04-16
Should I also change the *.xpm files?
Why there is both types there?

EDIT: **it works!**
I didn't even need to reboot.
Thank you for your help.

I leave the 3d open because I would like an answer on the *.xpm files.
I've currently overwritten the stock *.xpm files with the PNG icon I wanted to replace, maintaining the name. But I don't know if that's the right thing to do.

---

### Post by bapoumba on 2016-04-16
No knowledge about .xpm, keeping the name is important as the applications are going to look for a specific file. I hope you kept track of your edits and original files should you want to revert one day.
[https://en.wikipedia.org/wiki/X_PixMap](https://en.wikipedia.org/wiki/X_PixMap)
[http://www.fileformat.info/format/xpm/egff.htm](http://www.fileformat.info/format/xpm/egff.htm)

---

### Post by SamInside on 2016-04-16
> **bapoumba said:**
> keeping the name is important as the applications are going to look for a specific file.
Yes, but since the application will find a file that internally is a PNG, I don't think that's very good. Now everything is working, but...

> **bapoumba said:**
> I hope you kept track of your edits and original files should you want to revert one day.
Yes I renamed the originals to "*file_name.png**~***" with *mv*.

---

### Post by bapoumba on 2016-04-16
convert (see man convert) should do it, although from what I have seen, if you need transparency, you may not get the result you expect :)
[http://www.imagemagick.org/discourse-server/viewtopic.php?t=23129](http://www.imagemagick.org/discourse-server/viewtopic.php?t=23129)

---

