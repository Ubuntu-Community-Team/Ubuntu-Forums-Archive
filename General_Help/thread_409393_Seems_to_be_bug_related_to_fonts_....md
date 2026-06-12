---
title: "Seems to be bug related to fonts ..."
date: 2007-04-14
forum: General Help
---

### Post by ss0007 on 2007-04-14
Hi thr ,
I restored my fonts to default(sans) recently . When I look at it I can definitely see a 
difference in rendering . The font is not smooth as it looks when I first installaed ubuntu.
Pls take a look at the picture I have atached. I wanted to restore the font back original .
I have tried these
1) Set the Subpixel smoothing in Fonts window
2) Execute these script  ( and logout )
```
 mv ~/.gconf/desktop/gnome/interface/%gconf.xml ~/.gconf/desktop/gnome/interface/%gconf.old.xml
mv ~/.gconf/apps/nautilus/preferences/%gconf.xml ~/.gconf/apps/nautilus/preferences/%gconf.old.xml
mv ~/.gconf/apps/metacity/general/%gconf.xml ~/.gconf/apps/metacity/general/%gconf.old.xml

```

Still the same things . Is there anyway to restore these fonts back ?

Thanks in advance .

---

