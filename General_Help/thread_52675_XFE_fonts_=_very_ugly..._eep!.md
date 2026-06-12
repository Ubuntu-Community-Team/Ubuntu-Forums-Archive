---
title: "XFE fonts = very ugly... eep!"
date: 2005-07-28
forum: General Help
---

### Post by Swad on 2005-07-28
I installed the Hoary package for XFE (I think 0.66) and the fonts are not freetype at all.  They use the old system and are very rough edged.  Anyone have any ideas?

[http://www.zippyimages.com/files/78936/xfe.png](http://www.zippyimages.com/files/78936/xfe.png)

(I think you may need to copy and paste this to see it)

---

### Post by Psycho275 on 2005-07-28
Try this, Swad:

```
$ sudo apt-get install qt3-qtconfig
$ killall gnome-panel
```

Open System > Preferences > Qt Configuration

From there you can change the font, etc.

Let me know if that works.

---

### Post by mctavish on 2005-07-28
Yup, thats XFE. 

The latest versions of xfe have smooth fonts I believe. There was some talk of a backport IIRC. A forum search may give you more info.

---

### Post by Swad on 2005-08-01
qtconfig?  This uses the FOX tool-kit by the way, not Gnome or QT.  I did try it, but nothing changed the fonts.  Only reason I asked about the fonts was because a buddy running the build available to Gentoo had some nice looking GTK fonts in his, though I'm sure his was the latest version (the one in the Hoary repository isn't the latest).  Maybe latest can pull in the GTK theme on the computer.  I did see some posts about a backport.  I'll probably not worry about it much, though, as I really am used to not using a file manager in linux.

---

