---
title: "How to make snap apps visible under &quot;Other Applications&quot; when using &quot;Open with...&quot;?"
date: 2017-01-15
forum: General Help
---

### Post by clockb0x on 2017-01-15
I installed VLC from the Ubuntu Software application. This is apparently a snap app.  After install I had to log out and back in in order to get the icon to show up in the launcher.  Now I want to be able to select VLC when I right-click a video and select "Open with Other Application".  Unfortunately, it does not show up in the list of applications.  Some searching suggested this is a problem with the .desktop file, but the launcher seems to find it ok.  I'm not sure how it being a snap interacts with Ubuntu being able to list the app under Other Applications.  Has anyone run into this before?

---

### Post by deadflowr on 2017-01-16
vlc snap seems to be odd compared to other snaps in doing this.
(I have the krita snap installed and it is selectable from the open with dialog; unfortunately I have no other graphical snaps installed, only terminal based, so I cannot tell if krita is normal or unique.)

My solution was to simply create a desktop file, but with a small extra addition
```
[Desktop Entry]
Name=vlc-snap
Exec=/snap/bin/vlc %u
Type-Application
Icon=vlc
NoDisplay=true
```
save it in ~/.local/share/applications as something like vlc-snap.desktop

The small addition I added to mine was the NoDisplay option which will hide the new app from the menu system, but should allow it to show in the open with dialogs.
The icon setting is optional, but it'll add the icon to the selection options if you want.

See if that works for you.

*For what it is worth the snap  Exec line has the --started-from-file option, but i do not know whether this method would require it, since it ran without it fine.

If you plan on having multiple users with their own desktops being able to run this, then copy the file into the system applications folder at /usr/share/applications.

Hope it helps

---

### Post by howefield on 2017-01-16
> **clockb0x said:**
> This is apparently a snap app

Just to make sure that you are aware, there are 2 VLC packages in the repositories, the snap and also the "traditional" deb package that will behave as you would expect with regards your query. You are probably consciously running the snap package but just on the off chance that you aren't...

---

### Post by clockb0x on 2017-01-16
Thanks, that took care of it!

---

