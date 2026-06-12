---
title: "Panel Objects Rearranged"
date: 2008-06-23
forum: General Help
---

### Post by phildaman46 on 2008-06-23
Why do the objects on my panel keep getting rearranged when they are all locked to panel?

---

### Post by phildaman46 on 2008-06-24
Bump

---

### Post by VMC on 2008-06-24
Both the top and the bottom panels get rearranged or just one.

---

### Post by phildaman46 on 2008-06-24
I just have one panel and it's on the bottom. Heres a screenshot of how my panel should look like.

---

### Post by drs305 on 2008-06-24
Do you have the icons 'locked' in place? Right Click, Lock to Panel.

This sometimes doesn't prevent the icons from getting moved anyway. I save my panel information from time to time and when I restore them they are put back where the were before.

To save the panel settings (to a Desktop file named panels):
```
gconftool-2 --dump /apps/panel >~/Desktop/panels
```

To restore panel settings from the file ~/Desktop/panels (the killall command refreshes the desktop): 
```
 gconftool-2 --load ~/Desktop/panels && killall gnome-panel
```

---

### Post by renfrew on 2008-06-24
I've been having this problem too [http://ubuntuforums.org/showthread.php?t=838590](http://ubuntuforums.org/showthread.php?t=838590), only affects my top panel though.  Thanks to DRS305 for the workaround... now to get a fix...
n.b. Sorry for hijacking your thread phildaman46 but I couldn't find anything useful on launchpad or in other searches...

---

### Post by damis648 on 2008-06-24
This is a filed bug that happens when you change your resolution. Have you been changing your resolution when this happened?

---

### Post by phildaman46 on 2008-06-24
> **drs305 said:**
> Do you have the icons 'locked' in place? Right Click, Lock to Panel.

This sometimes doesn't prevent the icons from getting moved anyway. I save my panel information from time to time and when I restore them they are put back where the were before.

To save the panel settings (to a Desktop file named panels):
```
gconftool-2 --dump /apps/panel >~/Desktop/panels
```

To restore panel settings from the file ~/Desktop/panels (the killall command refreshes the desktop): 
```
 gconftool-2 --load ~/Desktop/panels && killall gnome-panel
```

Yes, my icons are all locked as I said on my first post.

> **damis648 said:**
> This is a filed bug that happens when you change your resolution. Have you been changing your resolution when this happened?

No I haven't changed my resolution. It has always been the same resolution, 1024x768.

---

