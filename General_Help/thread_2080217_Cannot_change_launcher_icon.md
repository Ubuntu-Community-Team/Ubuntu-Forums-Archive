---
title: "Cannot change launcher icon"
date: 2012-11-03
forum: General Help
---

### Post by woodyg on 2012-11-03
I am trying to change the launcher icon for Thunar to something more logical (an image of a folder), but what I'm doing isn't working. I have this in /usr/share/applications/Thunar.desktop

```
GenericName[ur_PK]=&#1601;&#1575;&#1574;&#1604; &#1605;&#1606;&#1740;&#1580;&#1585;
GenericName[zh_CN]=&#25991;&#20214;&#31649;&#29702;&#22120;
GenericName[zh_TW]=&#27284;&#26696;&#31649;&#29702;&#21729;
Exec=Thunar %F
**Icon=/home/me/stuff/custom_icons/Thunar.png**
Terminal=false
StartupNotify=true
Type=Application
Categories=System;Utility;Core;GTK;FileTools;FileManager;
```and have added a new icon (256x256 px png) to the directory indicated above. Why is it not working? :confused:

---

### Post by JKyleOKC on 2012-11-03
Have you rebooted since making the change? Some system configurations are changed only during the boot sequence. Others are changed at session login so need only logout/login to take effect. And still others change instantly when the config files are saved.

It would be worthwhile to check your home directory's .config directory (and other hidden files) to see if there's a local copy of the Thunar.desktop file taking precedence over the one in /usr/share, too...

---

### Post by woodyg on 2012-11-03
I'm still lost. :( I did remember that I had applied a patch to Thunar, so have a folder called thunar-1.2.3, which include desktop config file as well as icons. Don't know if any of those files are used, but better safe than sorry so I edited the config file and replaced the icons, but still no change (even after reboot). The .config folder contained a Thunar sub-folder, but I couldn't see any references to the icon in the 3 files in there. 

I did try to change another icon by editing the config file in usr/share/applications, and the icon changed without problem... so it seems the problem is with Thunar. Does it store config files in another location as well?

---

### Post by JKyleOKC on 2012-11-03
Good question, Woody; I don't know. I haven't found any other place, but I've not yet searched the whole file system...

---

### Post by Frogs Hair on 2012-11-03
If Alacarte is installed which includes the main menu the icon can be changed in launcher properties. Open launcher properties select the icon image and navigate to the desired image. Log out/in may be required.

---

