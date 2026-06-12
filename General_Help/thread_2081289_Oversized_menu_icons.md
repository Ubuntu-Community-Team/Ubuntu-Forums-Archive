---
title: "Oversized menu icons"
date: 2012-11-06
forum: General Help
---

### Post by Zvlwab on 2012-11-06
When I click on the Xfce4 menu, there are 2 icons that are larger than the other icons, which makes them render on top of other menu items. To be specific, they are Lone Survivor installed using software center and a custom Eclipse launcher using the eclipse icon provided by eclipse as downloadable on their website.

I have this issue since I did a fresh install of Xubuntu 12.10. I did not have this problem when running Xubuntu 12.04 with Xfce4.10 from the ppa.

---

### Post by eev2 on 2012-12-14
I have exactly the same problem. The icons for eclipse and gv.

---

### Post by Toz on 2012-12-15
gv seems to use a 50x50 pixmap as an icon. Have a look at the file /usr/share/applications/gv.desktop which states: 
> Icon=/usr/share/pixmaps/gv_icon.xpm
To fix this, you could change the icon to /usr/share/pixmaps/mini-gv.xpm (also included in the gv package)
```
Icon=/usr/share/pixmaps/mini-gv.xpm
```
...or any other icon file by editing the desktop file as root:
```
gksu leafpad /usr/share/applications/gv.desktop
```

The same might apply to eclipse. Have a look at /usr/share/applications/eclipse.desktop.

---

### Post by eev2 on 2012-12-15
Of you can do this but the point is that before the update the big icons were scaled to the correct size. I explicitly set in my .gtkrc-2.0 and .config/xfce4/.../xsettings.xml that I want 16x16 sizes but it doesn't obbey that.

---

### Post by Toz on 2012-12-15
Looks like a bug. See: [https://bugs.launchpad.net/ubuntu/+source/xfce4-panel/+bug/1066591]("https://bugs.launchpad.net/ubuntu/+source/xfce4-panel/+bug/1066591")

---

### Post by eev2 on 2012-12-17
I see. Thanks for the info. I guess there is not much to do.

---

